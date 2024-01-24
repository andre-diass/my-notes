
  
<h3> Key characteristics of the Singleton Pattern present in this code:</h3>

```TS
export class MongodbConnection {
  private static _connection?: MongoClient;
  private constructor() {}

  static async connection(uri: string, opts?: MongoClientOptions): Promise<MongoClient> {
    if (MongodbConnection._connection) {
      return MongodbConnection._connection;
    }

    MongodbConnection._connection = new MongoClient(uri, opts);
    return MongodbConnection._connection;
  }
}
```
<p> (1) Private Constructor: The singleton's constructor should always be private to prevent direct construction calls with the `new` operator</p>
<p> (2) Static Instance: The class contains a private static instance of itself (_connection), and a public static method (connection) is provided to access that instance.</p>
<p> (3) Lazy Initialization: The actual instance (_connection) is created only when it is requested for the first time. Subsequent requests return the already existing instance. </p>
<p> The Singleton Pattern is commonly used when a single point of control or coordination is required, and it helps in managing shared resources efficiently. 
  In this case, it ensures that there is only one connection to the database server throughout the application.</p>

<h3>Downfalls:</h3>
<p>The pattern requires special treatment in a multithreaded environment so that multiple threads won’t create a singleton object several times.</p>
<p> It may be difficult to unit test the client code of the Singleton because many test frameworks rely on inheritance when producing mock objects. 
  Since the constructor of the singleton class is private and overriding static methods is impossible in most languages, 
  you will need to think of a creative way to mock the singleton. Or just don’t write the tests. Or don’t use the Singleton pattern</p>
