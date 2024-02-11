# Tests: Unit testing

Created: October 15, 2023 12:02 PM
Updated: February 11, 2024 6:20 PM

*PART 1: THE BIGGER PICTURE*

CHAPTER 1: THE GOAL OF UNIT TESTING

```markdown
🔸DEFINITIONS:
🔹REGRESSION is when a feature stops working as intended after a certain
event (usually, a code modification). The terms regression and software bug
are synonyms and can be used interchangeably

```

```markdown
🔸A successful test suite has the following properties:
🔹 It’s integrated into the development cycle.
🔹 It targets only the most important parts of your code base.
🔹 It provides maximum value with minimum maintenance costs.

🔹Tests provide an early warning when you break existing functionality and
you become confident that your code changes won’t lead to regressions.

🔸In most applications, the most
important part is the part that contains business logic—the domain model.Testing
business logic gives you the best return on your time investment.

🔹All other parts can be divided into three categories:
- Infrastructure code
- External services and dependencies, such as the database and third-party systems
- Code that glues everything together

🔹Some of your tests, such as INTEGRATION TESTS, can go beyond the domain model and
verify how the system works as a whole

```

CHAPTER 2 : WHAT IS A UNIT TEST?

```markdown
🔸DEFINITIONS:
🔹UNIT TEST is an automated test that:
- Verifies a small piece of code (also known as a unit), (a single unit of behavior)
- Does it quickly,
- And does it in an isolated manner. (from other tests)

🔹TEST DOUBLE is an object that looks and behaves like its release intended
counterpart but is actually a simplified version that reduces the
complexity and facilitates testing

🔹METHOD UNDER TEST (MUT) is a method in the SUT called by the
test. The terms MUT and SUT are often used as synonyms, but normally, MUT
refers to a method while SUT refers to the whole class.

🔹The ARRANGE PART is where the tests make ready all dependencies and
the system under test. ACT PAHSE, where you
exercise the behavior you want to verify. The ASSERT STATEMENTS are the verification
stage, where you check to see if the behavior led to the expected results.

🔹SHARED DEPENDECIES: Dependencies that are accessible and used by multiple modules or components within an application.
These dependencies are typically accessible throughout the entire codebase. For example, a shared library or a
common utility function used across different modules in a software application.
🔹PRIVATE DEPENDECIES: Dependencies that are confined to a specific module or component and not accessible outside of that scope.
These dependencies are used internally within a module and are not meant to be shared with other parts of the application.
For example, a helper function or a local variable within a specific class that is not meant to be accessed by other components.
🔹OUT-OF-PROCESS DEPENDECIES: Dependencies that exist externally to the current application or process.
These dependencies are often utilized through inter-process communication mechanisms like APIs, web services,
or remote procedure calls. For example, when an application relies on data from an
external database or when it communicates with a web service to fetch information.

```

```
🔸The ISOLATION
issue is the root of the differences between the CLASSICAL and LONDON schools of
unit testing.

🔹THE LONDON SCHOOL describes isolation as isolating the system under test from its collaborators.It
means if a class has a dependency on another class, or several classes, you need to
replace all such dependencies with test doubles. This way, you can focus on the class
under test exclusively by separating its behavior from any external influence.

🔹In the CLASSICAL SCHOOL approach, it’s not the code that needs to be tested in
an isolated manner. Instead, unit tests themselves should be run in isolation from
each other. That way, you can run the tests in parallel, sequentially, and in any order,
whatever fits you best, and they still won’t affect each other’s outcome.
Isolating tests from each other means it’s fine to exercise several classes at once as
long as they all reside in the memory and don’t reach out to a shared state

🔹ISOLATING UNIT TESTS from each other entails isolating the class under test
from shared dependencies only. Private dependencies can be kept intact. Fig.1

🔹A unit doesn’t necessarily have to be limited to a class.
You can just as well unit test a group of classes, as long as none of them is a shared
dependency.

🔹THE DIFFERENCE between the London and classical schools is
the isolation attribute. The London school views it as isolation of the system under test
from its collaborators, whereas the classical school views it as isolation of unit tests
themselves from each other. Fig.2

🔹Tests shouldn’t verify units of code. Rather, TESTS SHOULD VERIFY units of
behavior: something that is meaningful for the problem domain and, ideally,
something that a business person can recognize as useful.

🔹THE LONDON SCHOOL considers any test that uses a real collaborator object an integration
test. Most of the tests written in the classical style would be deemed integration
tests by the London school proponents.

🔸An INTEGRATION TEST IS a test that doesn’t meet one of the three unit testing criteria.
For example, a test that reaches out to a shared dependency—say, a database—can’t run in isolation
from other tests. Finally, a test is an integration test when it verifies two or more units of behavior.

🔹In short, an INTEGRATION TEST IS a test that verifies that your code works in integration with
shared dependencies, out-of-process dependencies, or code developed by other teams
in the organization.

🔸END-TO-END (FUNCTIONAL TESTS) tests are a subset of integration tests. They too check to
see how your code works with out-of-process dependencies. The difference between an end-to-end
test and an integration test is that end-to-end tests usually include more of such dependencies.
The line is blurred at times, but in general, an integration test works with only one
or two out-of-process dependencies. On the other hand, an end-to-end test works with
all out-of-process dependencies, or with the vast majority of them.

🔹EXAMPLE: Let’s say your application works with three out-of-process dependencies: a database,
the file system, and a payment gateway. A typical integration test would include
only the database and file system in scope and use a test double to replace the payment
gateway. Fig.3

🔹Since END-TO-END tests are the most expensive in terms of maintenance, it’s better
to run them late in the build process, after all the unit and integration tests have
passed. You may possibly even run them only on the build server, not on individual
developers’ machines.

```

Fig.1 - Isolating_unit_tests

![Isolating_unit_tests](https://github.com/andre-diass/my-notes/assets/117690410/19e147a3-ac69-4e61-95a7-200f0b379edd)


Fig.2 - The_difference_of_schools 

![The_difference_of_schools](https://github.com/andre-diass/my-notes/assets/117690410/5f678a17-9f30-49a3-89ca-b23f4898a35f)


Fig.3 - End_to_end_tests

![End_to_end_tests](https://github.com/andre-diass/my-notes/assets/117690410/c0d966cb-4acb-45d0-a7e6-654324301e42)


*PART 2: MAKING YOUR TESTS WORK FOR YOU*

CHAPTER 4: THE FOUR PILLARS OF A GOOD UNIT TEST

```
🔸DEFINITIONS:
🔹A good UNIT TEST HAS the following FOUR ATTRIBUTES:
- Protection against regressions
- Resistance to refactoring
- Fast feedback
- Maintainability

🔹REFACTORING means changing existing code without modifying its
observable behavior. The intention is usually to improve the code’s nonfunctional
characteristics: increase readability and reduce complexity.

```

```
🔸PROTECTION AGAINST REGRESSIONS
🔹Code is not an asset is a liability

🔸RESISTANCE TO REFACTORING
🔹A FALSE POSITIVE is a false alarm. It’s a result
indicating that the test fails, although in reality, the functionality it covers works as intedend.

🔹WHAT CAUSES FALSES POSITIVES:
- Test that is coupled to the implementation details of the system
under test (SUT)

🔹We need to make sure the test verifies the end result the SUT delivers: its
observable behavior, not the steps it takes to do that. The best way to structure a test is to make
it tell a story about the problem domain.  Should such a test fail, that failure would mean
there’s a disconnect between the story  and the actual application behavior. Fig.1

🔸THERE IS A INSTRISIC CONNECTION BETWEEN
PROTECTION AGAINST REFGRESSIONS AND RESISTANCE TO REFACTORING:
- How good the test is at indicating the presence of bugs (lack of false negatives,
the sphere of protection against regressions)
- How good the test is at indicating the absence of bugs (lack of false positives,
the sphere of resistance to refactoring)

🔹FALSE POSITIVES are not as important initially because the importance of refactoring
is also not immediate; it increases gradually over time. You don’t need to conduct
many code clean-ups in the beginning of the project. Newly written code is often shiny
and flawless. It’s also still fresh in your memory, so you can easily refactor it even if
tests raise false alarms.  But as time goes on, the code base deteriorates. It becomes
increasingly complex and disorganized. Thus you have to start conducting regular refactorings
in order to  mitigate this tendency. Otherwise, the cost of introducing new features eventually
becomes prohibitive.

🔸Protection against regressions, resistance to refactoring, and fast feedback—
ARE MUTUALLY EXCLUSIVE. It’s impossible to maximize them all: you have to sacrifice one
of the three in order to max out the remaining two

🔹EXTREME CASE 1: END-TO-END TESTS:
- They provide the best protection against regressions
- End-to-end tests are also immune to false positives and thus have a good resistance
to refactoring. A refactoring, if done correctly, doesn’t change the system’s observable
behavior and therefore doesn’t affect the end-to-end tests.
- They don't have fast feedback

🔹EXTREME CASE 2: TRIVIAL TESTS:
Provide fast feedback. They also have low chance of producing a false positive, so they have good
resistance to refactoring. Trivial tests are unlikely to reveal any regressions, though,
because there’s not much room for a mistake in the underlying code.

🔹EXTREME CASE 3: TRIVIAL TESTS:
- The test  focuses on hows instead of whats and thus ingrains the SUT’s implementation
details, preventing any further refactoring.
- Similarly, it’s pretty easy to write a test that runs fast and has a good chance of catching
a regression but does so with a lot of false positives. Such a test is called a brittle test: it
can’t withstand a refactoring and will turn red regardless of whether the underlying
functionality is broken.

🔹The fourth attribute, MAINTANABILITY, is not correlated to the first three, with the exception
of end-to-end tests. End-to-end tests are normally larger in size because of the
necessity to set up all the dependencies such tests reach out to. They also require additional
effort to keep those dependencies operational. Hence end-to-end tests tend to
be more expensive in terms of maintenance costs.

🔹In reality, though, RESISTANCE TO REFACTORING is non-negotiable. You should aim at gaining
as much of it as you can, provided that your tests remain reasonably quick and you
don’t resort to the exclusive use of end-to-end tests. The trade-off, then, comes down
to the choice between how good your tests are at pointing out bugs and how fast they
do that: that is, between protection against regressions and fast feedback. You can view this
choice AS A SLIDER THAT CAN BE FREELY MOVED BETWEEN PROTECTION AGAINST REGRESSION
AND FAST FEEDBACK. The more you gain in one attribute, the more you lose on the other. Fig.3

🔹The reason resistance to refactoring is non-negotiable is that whether a test possesses
this attribute is mostly a binary choice: the test either has resistance to refactoring or it
doesn’t. There are almost no intermediate stages in between.

```

Fig.1 - Testing_end_results

![Testing_end_results](https://github.com/andre-diass/my-notes/assets/117690410/df1ede5f-e29c-4761-9709-05afb3beb4be)


Fig.2 - End_to_end_test_and_trivial_tests


![End_to_end_test_and_trivial_tests](https://github.com/andre-diass/my-notes/assets/117690410/a5ab8d3f-b57a-48f1-80cd-d1ee768a826f)

Fig.3 - The_trade_off_between_the_attributes_of_a_good_unit_testing

![The_trade_off_between_the_attributes_of_a_good_unit_testing](https://github.com/andre-diass/my-notes/assets/117690410/7c57dfbc-6e27-4a72-91a3-f99568c452e8)


Fig.4 - Breaking_down_the_test_pyramid

![Breaking_down_the_test_pyramid](https://github.com/andre-diass/my-notes/assets/117690410/0cc4753d-2bd3-4ee2-ac8e-6d53d18257d4)


```
🔸There are EXCEPTIONS TO THE TEST PYRAMID.
- For example, if all your application does
is basic create, read, update, and delete (CRUD) operations with very few business
rules or any other complexity, your test “pyramid” will most likely look like a rectangle
with an equal number of unit and integration tests and no end-to-end tests.

- Unit tests are less useful in a setting without algorithmic or business complexity—
they quickly descend into trivial tests.

- Another exception to the Test Pyramid is an API that reaches out to a single out-ofprocess
dependency—say, a database. Having more end-to-end tests may be a viable
option for such an application. Since there’s no user interface, end-to-end tests will
run reasonably fast

```

CHAPTER 5: MOCKS AND TEST FRAGILITY

```
🔸DEFINITIONS:
🔹TEST DUBLE is an overarching term that describes all kinds of non-production-ready,
fake dependencies in tests. Fig.1

🔸All production code can be categorized along two dimensions:
- Public API vs. private API (where API means application programming interface)
- Observable behavior vs. implementation details

🔹Most programming languages provide a simple mechanism to differentiate between
the code base’s public and private APIs. For example, in C#, you can mark any member
in a class with the private keyword, and that member will be hidden from the client
code, becoming part of the class’s private API. The same is true for classes: you can
easily make them private by using the private or internal keyword.

🔹THE DISTINCTION BETWEEN OBSERVABLE BEHAVIOR AND IMPLEMENTATION DETAILS
is more nuanced. For a piece of code to be part of the system’s observable behavior, it
has to do one of the following things:
- Expose an operation that helps the client achieve one of its goals. An operation is
a method that performs a calculation or incurs a side effect or both.
- Expose a state that helps the client achieve one of its goals. State is the current
condition of the system.
ANY CODE THAT DOES NEITHER OF THESE TWO THINGS IS AN IMPLEMENTATION DETAIL

```

```
🔸The DIFFERENCE BETWEEN MOCKS AND STUBS is that:
- MOCKS help to EMULATE and EXAMINE outcoming interactions. These interactions
are calls the SUT makes to its dependencies to change their state.
- STUBUS help to EMULATE incoming interactions. These interactions are calls the
SUT makes to its dependencies to get input data Fig.2

- You can refer to the classes from mocking libraries as mocks, too.

🔹Classes from mock libraries help you create actual mocks, but they themselves are
not mocks per se. It’s important not to conflate a mock (the tool) with a mock (the test double)
because you can use a mock (the tool) to create both types of test doubles: mocks and stubs.

🔹A call from the SUT to a stub is not part of the end result the SUT produces.
Such a call is only a means to produce the end result: a stub provides
input from which the SUT then generates the output

🔸The notions of mocks and stubs tie to the COMMAND QUERY SEPARATION (CQS) principle.
The CQS principle states that EVERY METHOD SHOULD BE EITHER A COMMAND OR A QUERY
but not both. As shown in Fig.3, commands are methods that produce side
effects and don’t return any value (return void). Examples of side effects include
mutating an object’s state, changing a file in the file system, and so on. Queries are the
opposite of that—they are side-effect free and return a value.
To follow this principle, be sure that if a method produces a side effect, that
method’s return type is void. And if the method returns a value, it must stay side-effect
free. In other words, asking a question should not change the answer. Code that maintains
such a clear separation becomes easier to read. You can tell what a method does
just by looking at its signature, without diving into its implementation details.
Of course, it’s not always possible to follow the CQS principle. There are always
methods for which it makes sense to both incur a side effect and return a value.

🔸The use of mocks is beneficial when verifying the communication pattern between
your system and external applications. Conversely, using mocks to verify communications
between classes inside your system results in tests that couple to implementation
details and therefore fall short of the resistance-to-refactoring metric

```

```
🔸By making all implementation details private, you leave your tests no
choice other than to verify the code’s observable behavior, which automatically
improves their resistance to refactoring.

🔹Another guideline flows from the definition of a well-designed API: you should expose
the absolute minimum number of operations and state. Only code that directly helps
clients achieve their goals should be made public. Everything else is implementation
details and thus must be hidden behind the private API.

🔸Hexagonal Archiecture
🔹A typical application consists of two layers, DOMAIN AND APPLICATION SERVICES, as
shown in figure 4. The domain layer resides in the middle of the diagram because
it’s the central part of your application. It contains the business logic: the essential
functionality your application is built for.

🔹The combination of the application services layer and the domain layer forms a hexagon,
which itself represents your application. It can interact with other applications,
which are represented with their own hexagons (see figure 5.9). These other applications
could be an SMTP service, a third-party system, a message bus, and so on. A set
of interacting hexagons makes up a hexagonal architecture

🔹The term hexagonal architecture was introduced by Alistair Cockburn. Its purpose is to
emphasize three important guidelines:
- The separation of concerns between the domain and application services layers
- Communications inside your application. Classes inside the domain layer should only depend on each other; they
should not depend on classes from the application services layer.
- Communications between applications

🔹Each layer of your application exhibits observable behavior and contains its own set of
implementation details. For example, observable behavior of the domain layer is the
sum of this layer’s operations and state that helps the application service layer achieve
at least one of its goals

🔹When you make each layer’s API well-designed (that is, hide its implementation
details), your tests also start to have a fractal structure; they verify behavior that helps
achieve the same goals but at different levels. A test covering an application service
checks to see how this service attains an overarching, coarse-grained goal posed by the
external client. At the same time, a test working with a domain class verifies a subgoal
that is part of that greater goal Fig.5

🔹For a piece of code to be part of observable behavior,
it needs to help the client achieve one of its goals. For a domain class, the client is
an application service; for the application service, it’s the external client itself.

🔸There are two types of communications in a typical application: INSTRA-SYSTE AND INTER-SYSTEM.
Intra-system communications are communications between classes inside your
application. Inter-system communications are when your application talks to other applications

🔹Intra-system communications are implementation details; inter-system
communications are not.

🔹Intra-system communications are implementation details because the collaborations
your domain classes go through in order to perform an operation are not part of their
observable behavior. These collaborations don’t have an immediate connection to the
client’s goal. Thus, coupling to such collaborations leads to fragile tests.

🔹Inter-system communications are a different matter. Unlike collaborations between
classes inside your application, the way your system talks to the external world forms
the observable behavior of that system as a whole. It’s part of the contract your application
must hold at all times Fig.6 The call to the SMTP service is a legitimate reason to do mocking. It doesn’t lead
to test fragility because you want to make sure this type of communication stays in
place even after refactoring. The use of mocks helps you do exactly that

```

Fig.1 - Types_of_test_doubles

![Types_of_test_doubles](https://github.com/andre-diass/my-notes/assets/117690410/6c877397-dfc5-4553-8a03-0c0011b4a5dd)


Fig.2 - The_difference_between_test_doubles

![The_difference_between_test_doubles](https://github.com/andre-diass/my-notes/assets/117690410/4f4ca074-a810-4ed9-8b5f-ccba52bd2e4a)


Fig.3 - The_command_query_separation

![The_command_query_separation](https://github.com/andre-diass/my-notes/assets/117690410/c9f59f57-9461-40e8-aeb0-2148ae7d510a)


Fig. 4 - Hexagonal_Architecture

![Hexagonal_Architecture](https://github.com/andre-diass/my-notes/assets/117690410/084a1236-170e-4a7b-a0f2-4c003064619d)


Fig. 5 - Fractural_Structure_of_tests 

![Fractural_Structure_of_tests](https://github.com/andre-diass/my-notes/assets/117690410/e21ab83d-c2b5-45f6-8cda-4ef03813a099)


CHAPTER 6: STYLES OF UNIT TESTING

```
🔸FUNCTIONAL PROGRAMMING is programming with mathematical functions. A mathematical
function (also known as pure function) is a function (or method) that doesn’t have
any hidden inputs or outputs. All inputs and outputs of a mathematical function must
be explicitly expressed in its method signature, which consists of the method’s name,
arguments, and return type. A mathematical function produces the same output for a
given input regardless of how many times it is called

🔸FUNCTIONAL ARCHITECTURE maximizes the amount of code written in a
purely functional (immutable) way, while minimizing code that deals with
side effects. The goal of functional programming is not to eliminate side effects altogether but
rather to introduce a separation between code that handles business logic and code
that incurs side effects

```

```
🔸OUTPUT-BASED STYLE: where you feed an input to the system
under test (SUT) and check the output it produces. This style of unit
testing is only applicable to code that doesn’t change a global or internal state, so the
only component to verify is its return value

🔸STATE BASED STYLE is about verifying the state of the system after an operation is complete.
The term state in this style of testing can refer to the state of the
SUT itself, of one of its collaborators, or of an out-of-process dependency, such as
the database or the filesystem.

🔸COMMUNICATION BASED TESTING This style uses
mocks to verify communications between the system under test and its collaborators

🔸Comparing the styles using the metrics of protection against
regressions

🔹The metric of protection against regressions doesn’t depend
on a particular style of testing. This metric is a product of the following three
characteristics:
- The amount of code that is executed during the test
- The complexity of that code
- Its domain significance

🔹Generally, you can write a test that exercises as much or as little code as you like; no
particular style provides a benefit in this area. The same is true for the code’s complexity
and domain significance. The only exception is the communication-based
style: overusing it can result in shallow tests that verify only a thin slice of code and
mock out everything else

🔸Comparing the styles using the metric of resistance
to refactoring

🔹output based > state based > communication based
🔹You can reduce the number of false positives to a minimum by
maintaining proper encapsulation and coupling tests to observable behavior only.
Admittedly, though, the amount of due diligence varies depending on the style of
unit testing.

🔸Comparing the styles using the metric of maintainability
Maintainability evaluates the unit tests’ maintenance costs and is defined by the
following two characteristics (it does not correlate to the style):
- How hard it is to understand the test, which is a function of the test’s size
- How hard it is to run the test, which is a function of how many out-of-process
dependencies the test works with directly

```

```
🔸FUNCTIONAL ARCHITECTURE AND TESTING:

🔹Explicit inputs and outputs make mathematical functions extremely testable because
the resulting tests are short, simple, and easy to understand and maintain. Mathematical
functions are the only type of methods where you can apply output-based
testing, which has the best maintainability and the lowest chance of producing a
false positive.

🔹On the other hand, hidden inputs and outputs make the code less testable (and
less readable, too). Types of such hidden inputs and outputs include the following:
- Side effects—A side effect is an output that isn’t expressed in the method signature
and, therefore, is hidden. An operation creates a side effect when it mutates the
state of a class instance, updates a file on the disk, and so on.
- Exceptions—When a method throws an exception, it creates a path in the program
flow that bypasses the contract established by the method’s signature. The
thrown exception can be caught anywhere in the call stack, thus introducing an
additional output that the method signature doesn’t convey.
- A reference to an internal or external state—For example, a method can get the current
date and time using a static property such as DateTime.Now. It can query
data from the database, or it can refer to a private mutable field. These are all
inputs to the execution flow that aren’t present in the method signature and,
therefore, are hidden.

🔸In FUNCTIONAL ARCHITECTURE,
The separation between business logic and side effects is done by segregating two
types of code:
- Code that makes a decision—This code doesn’t require side effects and thus can
be written using mathematical functions.
- Code that acts upon that decision—This code converts all the decisions made by
the mathematical functions into visible bits, such as changes in the database or
messages sent to a bus.
The code that makes decisions is often referred to as a functional core (also known as an
immutable core). The code that acts upon those decisions is a mutable shell. FIG.1

🔹In HEXAGONAL ARCHITECTURE,
classes inside the domain layer should only depend on each other; they should

not depend on classes from the application services layer. Likewise, the immutable

core in functional architecture doesn’t depend on the mutable shell. It’s self-sufficient

and can work in isolation from the outer layers. This is what makes functional architecture

so testable: you can strip the immutable core from the mutable shell entirely

and simulate the inputs that the shell provides using simple values.

🔹THE DIFFERENCE BETWEEN THE TWO is in their treatment of side effects. Functional
architecture pushes all side effects out of the immutable core to the edges of a business

operation. These edges are handled by the mutable shell. On the other hand, the

hexagonal architecture is fine with side effects made by the domain layer, as long as

they are limited to that domain layer only. All modifications in hexagonal architecture

should be contained within the domain layer and not cross that layer’s boundary. For

example, a domain class instance can’t persist something to the database directly, but

it can change its own state. An application service will then pick up this change and

apply it to the database.

```

Fig.1 - Functional_Architecture

![Functional_Architecture](https://github.com/andre-diass/my-notes/assets/117690410/663a227b-cfd7-46f4-8d4c-264ca91c8d95)


CHAPTER 6: REFACTORING TOWARD VALUABLE UNIT TESTS

```
🔸All production code can be categorized along three dimensions:
- Complexity
- Domain significance
- The number of collaborators

🔹CODE COMPLEXITY is defined by the number of decision-making (branching) points in the
code. The greater that number, the higher the complexity.

🔹DOMAIN SIGNIFICANCE shows how significant the code is for the problem domain of your
project. Normally, all code in the domain layer has a direct connection to the end

users’ goals and thus exhibits a high domain significance

🔹Complex code and code that has domain significance benefit from unit testing the
most because the corresponding tests have great protection against regressions.

🔹COLLABORATOR is a dependency that is either
mutable or out-of-process (or both). Code with a large number of collaborators is

expensive to test. The type of the collaborators also matters. Out-of-process
collaborators are a no-go
when it comes to the domain model. They add additional
maintenance costs due to the necessity to maintain complicated mock machinery in tests.

🔹The combination of code complexity, its domain significance, and the number of

collaborators give us the four types of code shown in FIG.1

```

FIG.1 - The_four_types_of_code

![The_four_types_of_code](https://github.com/andre-diass/my-notes/assets/117690410/1f09e567-cabd-44ce-9183-2425c048f35f)


FIG.2 - Hexagonal_Architecture_and_types_of_code

![Hexagonal_Architecture_and_types_of_code](https://github.com/andre-diass/my-notes/assets/117690410/16e9e369-db93-41fd-82c2-b8c4a66f25e9)
