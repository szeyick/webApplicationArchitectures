## Web Service Processes and Composition

1. A Flow Model in a service workflow shows

  - How data flows from service to service
  - The order in which activities are executed
  - The flow of error handling or compensation
  - None of the above

**Answer** - The flow model shows the order in which activities are executed. The links between them can be used to show how data flows but generally it is used to describe how activites are combined.

2. A workflow is just another name for a business process.

  - True
  - False
  
**Answer** - Workflow describes how the activity or data flows through a system. A business process is a horizontal view of a business that describes processes as activities to produce an output for a customer or market, it is a higher level view.

3. An advantage of an orchestrated approach over an event-driven approach is that is easier to add extra activities

  - True
  - False

**Answer** - The orchestrated approach is activity centric approach, where we describe each activity and the data passed between each. An event driven approach we can use a flow chart to describe how control is passed through. It is easier to add extra activities to an event driven approach.

4. Tick all of the following answers that are correct. Computerised control of workflow necessarily requires

  - Making decisions that determine the flow of control
  - Tracking the state of a process instance
  - Progressing instance state in a controlled way
  - Runtime adaptation of  the process definition
  
**Answer** - Computerised workflow is the process of defining a workflow in a logical step by step manner. All of the above except for "Runtime adaptation of  the process definition" is in computerised workflow.

5. How does an asynchronous service orchestration fundamentally differ from a program executed in, say, Java? (there may be more than correct answer)

  - The key data type is the message
  - Flow control is based on transition conditions 
  - There is no difference other than in orchestration the communication is between services, and in Java the communication is between objects 
  - The process enactment is driven by events
  
**Answers** - Service orchestration is activity centric, this means that flow control means the passing of data (messages) between services or activities. Java on the other hand uses objects that are passed around.

6. Associate the following terms process that are either

A. Centralised-view of process or B. Decentralised-view of process

  - Orchestration
  - Choreography
  - Event-driven
  - HATEOAS
  
**Answer** - 

  - Orchestration - **A**
  - Choreography - **B**
  - Event-driven - **B**
  - HATEOAS - **B**
  
7. To create a RESTful process the server returns to the client:

  - The requested data and a function to determine the next step in the process
  - The requested data only
  - The requested data plus a (list of) hyperlinks to the next step(s) in the process
  - The requested data and the state of the process instance
  
**Answer** - RESTful processes (HATEOAS) use HTTP (CRUD) commands as per usual, but on the return message along with the requested data, the service also returns a list of links to allow the client to choose which activity to execute next.

8. Match the process characteristic with either 

1. a routine workflow or 2. a knowledge-intensive process

  - Complete process definition
  - Goal rather than task oriented
  - Process instance needs to be adapted 
  - Centralised decision making

**Answer** -

  - Complete process definition - **A**
  - Goal rather than task oriented - **B**
  - Process instance needs to be adapted  - **B**
  - Centralised decision making - **A**
  
9. Which of the following statements are true. (There may be more than one correct answer)

A service composition

  - Is the same thing as a service mashup
  - Is the same thing as a service orchestration
  - Is a service that invokes other services
  - Is a service client that invokes a number of services
  
**Answer** - 

A service composition

  - Is the same thing as a service mashup - **FALSE**
  - Is the same thing as a service orchestration - **FALSE**
  - Is a service that invokes other services - **TRUE**
  - Is a service client that invokes a number of services - **FALSE**
  
10. Which of the following process languages are

1. Executable or 2. Non-executalbe modeling languages 

  - BPEL - Business Process Execution Language.
  - WS-CDL - Choreography Description Language.
  - EPC 
  - BPMN - Business Processing Modelling Notation.
  
**Answer** - Only BPEL is executable, the others are used for definition.



