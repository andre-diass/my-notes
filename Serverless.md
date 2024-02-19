# Serverless

Tags: toPutOnRemote
Created: July 13, 2023 10:23 AM
Updated: February 18, 2024 9:24 PM

```
Stage
stage: ${opt:stage, 'dev'}
serverless deploy --stage production
The stage variable will be set to 'production'.
, 'dev': This part sets a default value of 'dev' for the stage if it's not explicitly provided. So, if you run Serverless commands without specifying the stage, it will be set to 'dev' by default.

Invoke Function
Invokes an AWS Lambda Function on AWS and returns logs.
serverless invoke -f [FUNCTION NAME] -s [STAGE NAME] -r [REGION NAME] -l

Streaming Logs
Open up a separate tab in your console and stream all logs for a specific Function using this command.
serverless logs -f [FUNCTION NAME] -s [STAGE NAME] -r [REGION NAME]
```

DYNAMIC OPERATORS

**${self:<variable>}:** where a variable is a variable on the yml file

**${param:<variable>}:** These are used to reference parameters defined either in the yml file or provided externally

**${file(.<file path>}:** This is used to read the contents of a file

**${env:<variable name>}**: This is used to reference environment variables.

**${ssm:/path/to/parameter}**: This is used to reference AWS Systems Manager (SSM) parameters

**${opt:stage}**: This is used to reference command-line options passed during deployment.

**{ Ref: <resource name> }:** This is a CloudFormation reference to the logical ID of a resource name. It's used to access the value of a resource, typically defined elsewhere in the yml file.

PASSO A PASSO DE INTEGRAÇÃO COM UM SERVIÇO

Cria um recurso > da permissão pra o recurso > associa como gatilho de uma função

### Skeleton

```
service:
  # Will be the stack name
  name: myservice
provider:
  name: aws
  runtime: nodejs12.x
  tracing:
    # Enable AWS XRay
    lambda: true
    apiGateway: true
  # Give lambda permissions to access resources.
  iamRoleStatements:
    # See: IAM Role Statements
  environment:
    # Usually !Ref is what you need to use a resource with the
    # AWS clients and you can put them in environment variables.
    MyQueueResource: !Ref MyQueueResource
functions:
  # See: Functions
resources:
  Resources:
    # Arbitrary CloudFormation.
  Outputs:
    # Outputs.

```

## IAM Role Statements

**serverless.yml**

```
provider:
  iamRoleStatements:
    - Effect: Allow
      Action: ["sqs:*"]
      Resource:
        # Most things are !GetAtt Something.Arn
        - !GetAtt MyQueueResource.Arn
    - Effect: Allow
      Action: ["sns:*"]
      Resource:
        # Some things use !Ref instead of !GetAtt for the arn. See CloudFormation docs.
        - !Ref MySnsTopic

```

## Functions

**serverless.yml**

```
functions:
  startSomeTask:
    handler: handler.startSomeTask
    events:
      # See: Events

```

### Event: API Gateway

**serverless.yml**

```
functions:
  apiHandler:
    handler: handler.apiHandler
    events:
      - http:
          path: /route/{paramName}
          method: post

```

**handler.ts**

```
import { APIGatewayProxyHandler, APIGatewayProxyResult } from "aws-lambda";

export const apiHandler: APIGatewayProxyHandler = async (
  event: APIGatewayEvent,
  _context: APIGatewayEventRequestContext
): Promise<APIGatewayProxyResult> => {
  {
    statusCode: 200,
    body: JSON.encode({
      routeParamName: event.pathParameters.paramName,
      requestId: _context.requestId,
    }),
  };
};

```

### Event: SQS

**serverless.yml**

```
functions:
  queueTrigger:
    handler: dist.queueTrigger
    events:
      - sqs:
          arn: !GetAtt MyQueue.Arn
          # One record at a time.
          batchSize: 1

```

**handler.ts**

```
import { SQSHandler, SQSRecord, SQSEvent } from "aws-lambda";

export const startCheckTaskFromTaskQueue: SQSHandler = async (
  event: SQSEvent
): Promise<void> => {
  await Promise.all(
    event.Records.map(async (record: SQSRecord) => {
      const messageBody = JSON.parse(record.body);
    })
  );
};
```

SQS

o gerenciamento de receber e apagar as mensagens da fila são feitos ‘automaticamente’ no ambiente serverless. no ambiente com servidor isso precisa ser feito atraves da sdk do serviço de forma explicita 

```yaml
resources:
  Resources:
    FilaAcessos:
      Type: AWS::SQS::Queue
      Properties:
        QueueName: acesso.fifo
        FifoQueue: true
        SqsManagedSseEnabled: false
        RedrivePolicy:
          deadletterTargetArn:
            Fn::GetAtt:
              - DlqAcessos
              - Arn
          maxReceiveCount: 5
        VisibilityTimeOut: 10
    DlqAcessos:
      Type: AWS::SQS::Queue
      Properties:
        QueueName: acesso-dlq.fifo
        FifoQueue: true
        SqsManagedSseEnabled: false
				MessageRetentionPeriod: 86400
```

maxReceiveCount: 5 ⇒ quantas mensagens minha fila principal vai tentar refazer antes de mandar a msg pra dql

visibilityTimeOut: 10 ⇒ quanto tempo de intervalo entre essas mensagens de retry. tem quer ser no minimo 5/6x maior que o timeout da função engatilhada

MessageRetentionPeriod: 86400 ⇒ tempo que a mensagem vai ficar na dlq. tempo de um dia em segundos

LEMBRA QUE: eu posso adicionar uma lambda pra ser chamada com gatilho da dlq. essa lambda pode implementar oq eu quiser, inclusive chamar outra queue.

```yaml
acessoConsumer:
    handler: src/functions/consumers/acessoConsumer.handler
    events:
      - sqs:
          arn:
            Fn::GetAtt:
              - FilaAcessos
              - Arn
          batchSize: 1
					maximumConcurrency: 10
		timeout: 2
```

batchSize: 1 ⇒ enviar mensagens em lote ou nao

maximumConcurreny: quantas lambdas quero executar simultaneamente pra processar as mensagens. lembrar que isso vai significar requisiçoes em paralelo se eu tiver integrando com serviços externos ou internos. O valor máximo definido na propriedade vai limitar o número de instâncias simultâneas de uma função que podem ser chamadas (ou invocadas) por um evento SQS. O valor mínimo é `2` e o máximo `1000`. Caso não queira configurar um limite, basta não acrescentar a propriedade para que a AWS Lambda trabalhe sempre com a quantidade máxima de instâncias simultâneas (`1000`). 

In a serverless environment using Amazon Simple Queue Service (SQS), messages may not be delivered and can end up in a Dead Letter Queue (DLQ) due to various reasons. Here are some common scenarios:

1. **Message Retention Period Exceeded:**
    - If a message stays in the queue longer than the configured retention period (maximum of 14 days), it will be moved to the DLQ.
2. **Visibility Timeout Exceeded:**
    - When a consumer retrieves a message from the queue, it becomes temporarily invisible to other consumers for a specified visibility timeout period. If the consumer fails to process and delete the message within this time frame, the message becomes visible again. If this happens repeatedly (exceeding the maximum receive count), the message is moved to the DLQ.
3. **Consumer Error Handling:**
    - If there's an error in the consumer's processing logic and it doesn't handle the error correctly (e.g., doesn't catch exceptions), the message may not be deleted from the queue. After reaching the maximum receive count, the message gets moved to the DLQ.
4. **Message Size Limit:**
    - If a message size exceeds the maximum allowed limit for the queue, it will not be delivered and may be sent to the DLQ.
5. **Queue Overflow:**
    - If the queue is at its maximum capacity and cannot accept more messages, new messages may not be delivered and might end up in the DLQ.
6. **Permissions and Access Issues:**
    - If the consumer or the process managing the queue doesn't have the necessary permissions to read from or write to the queue, messages may not be delivered. Ensure that the appropriate IAM roles and policies are correctly configured.
7. **Queue Deletion:**
    - If the SQS queue is deleted while there are still messages in it, those messages will be sent to the DLQ if configured.
8. **Redundant/Duplicate Messages:**
    - If duplicate messages are sent to the queue, and the consumer is unable to process them correctly, it may lead to messages being sent to the DLQ.
9. **Message Time-To-Live (TTL) Exceeded:**
    - If a message has a TTL set, and it stays in the queue longer than the TTL, it will be moved to the DLQ.
