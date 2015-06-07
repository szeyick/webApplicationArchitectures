## Event Driven Architectures -

1. Event driven architectures are typically used to create applications that are:

  - Request-Response messaging
  - Sense and Respond
  - Command driven
  - RESTful
  
**Answers** - Sense and Response applications are usually good candidates for EDA. The others are generally good for SOA.

2. Which of the following of the applications would be suitable for an EDA? (more than one answer may be correct)

	- A military situational awareness application
  - Commodity trading
  - Data stream processing
  - A home sensor network

**Answers** - All the applications listed above would be good for EDA, the reason being is that they are all applications that would require responding to events.

3. An event in an EDA application is

	- Anything that affects the application
  - Anything that affects the user of the application
  - Some occurance that the system senses and is defined of as of interest to the application 
  - Anything the system can measure 
  
**Answers** - Some occurance that the system senses and is defined of as of interest to the application. 

4. Select the best answer. A complex event in EDA 

  - Is a event that requires a complex data structure to record it.
  - All events can be complex. It depends on the context in which they are used.
  - Is an event that has a temporal aspect.
  - Is an event that is inferred from relationships between other events
  
**Answers** - Is an event that is inferred from relationships between other events

5. Which of the following are event processing styles in EDA (more than one answer may be correct)

	- Simple Event Processing
  - Sensor  Event Processing
  - Stream Event Processing
  - Complex Event Processing
  
**Answer** - Simple, Stream and Complex events are processing styles in EDA.

6. Categorise each of the following attributes as either typical of a 

(i) Traditional database application
or
(ii) CEP application

  - Queries are run continuously
  - Evaluation of query triggered by query submission
  - Graph based databases
  - Suited to thousands of queries per second

A.	CEP
B.	Traditional database app

**Answer** - 

  - Queries are run continuously - **Complex Event Process**
  - Evaluation of query triggered by query submission - **Traditional Database Application**
  - Graph based databases - **Complex Event Process** - CEP are good for No-Sql databases.
  - Suited to thousands of queries per second - **Complex Event Process**
  
7. For a topic in a pub-sub network, place the following activities in the correct order  

  - Publisher notifies the local broker of an event matching the topic 
  - Client receives data matching the subscription query
  - Topic advertisement is propogated to other brokers
  - Publisher advertisers a topic to local broker
  
**Answer** - 4, 3, 2, 1

8. Match the following characteristics to either:

1: Event driven communication or  2: Request-response communication

  - Decoupled
  - Parallel execution 
  - Interaction instance intiated by client
  - Sender of information does not care what happens to it

A.	Event-driven
B.	Request-response

**Answer** - 

  - Decoupled - **A**
  - Parallel execution - **A**
  - Interaction instance intiated by client - **B**
  - Sender of information does not care what happens to it - **A**
  
9. Which of the following WS* standards directly supports event driven messaging?

  - WS-Notification
  - WS-PubSub
  - WS-Routing
  - No Web Service standards support EDA. They are only designed to support SOA. 

**Answer** - Which of the following WS* standards directly supports event driven messaging?

10. Select which of the following are true statements regarding rule engines and EDA (there may be more than one)

	- Rules engines can be used to filter simple events
  - Rules engines often reside in an ESB
  - Rules engines are used to correlate simple events into complex events 
  - Rules engines can be used to generate events
  
**Answers** - All of the above.
