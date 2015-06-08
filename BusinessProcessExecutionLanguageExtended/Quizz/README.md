## BPEL Quizz -

1. A Flow Model in a service workflow shows

	- How data flows from service to service
  - The order in which activities are executed
  - The flow of error handling or compensation
  - None of the above
  
**Answer** - The order in which activities are executed

2. A workflow is just another name for a business process.
  
  - True
  - False

**Answer** - False

3. An advantage of an orchestrated approach over an event-driven approach is that is easier to add extra activities
  
  - True
  - False
  
**Answer** - False

4. Tick all of the following answers that are correct. Computerised control of workflow necessarily requires

	- Runtime adaptation of  the process definition
  - Making decisions that determine the flow of control
  - Tracking the state of a process instance
  - Progressing instance state in a controlled way
  
**Answer** - 

  - Making decisions that determine the flow of control
  - Tracking the state of a process instance
  - Progressing instance state in a controlled way
  
5. How does an asynchronous service orchestration fundamentally differ from a program executed in, say, Java? (there may be more than correct answer)

	- The process enactment is driven by events
  - Flow control is based on transition conditions 
  - There is no difference other than in orchestration the communication is between services, and in Java the communication is between objects 
  - The key data type is the message
  
**Answer** - 
  - The key data type is the message
  - Flow control is based on transition conditions 
  	
6. Associate the following terms process that are either

A. Centralised-view of process or B. Decentralised-view of process

  - Orchestration
  - Choreography
  - Event-driven
  - HATEOAS
  
**Answer** - Only orchestration (BPEL) is a centralised view of a process.

7. To create a RESTful process the server returns to the client:

	- The requested data only
  - The requested data and the state of the process instance
  - The requested data plus a (list of) hyperlinks to the next step(s) in the process
  - The requested data and a function to determine the next step in the process

**Answer** - The requested data plus a (list of) hyperlinks to the next step(s) in the process

8. Match the process characteristic with either 

1. a routine workflow or 2. a knowledge-intensive process

  - Complete process definition
  - Goal rather than task oriented
  - Process instance needs to be adapted 
  - Centralised decision making
  
**Answer** - 

  - Complete process definition - **A**
  - Goal rather than task oriented - **B**
  - Process instance needs to be adapted - **B** 
  - Centralised decision making - **A**
  
9.  Which of the following statements are true. (There may be more than one correct answer)

A service composition

	- Is the same thing as a service orchestration
  - Is the same thing as a service mashup
  - Is a service that invokes other services
  - Is a service client that invokes a number of services
  
**Answer** - Is a service that invokes other services

10. Which of the following process languages are

1. Executable or 2. Non-executalbe modeling languages 

  - BPEL
  - WS-CDL
  - EPC
  - BPMN

**Answer** - Only BPEL is executable.

11. A "partner" in a BPEL process is:
	
	- Activity that communicates with another activity
	- Another BPEL process that uses an abstract interface of the original process
	- Another service that interact via a basic activity with the process
	- A typed connector
	
**Answer** - Another service that interact via a basic activity with the process

12. A Flow Model in a service workflow shows
	
	- How data flows form service to service
	- The order in which activities are executed
	- The flow of error handling or compensation
	- None of the above
	
**Answer** - The order in which activities are executed.

13. A message to what activity(ies) can create a new instance of a process?
	
	- Any activity.
	- Any basic activity.
	- Invoke activity
	- Receive or pick activity
	- Create instance activity
	
**Answer** - Receive or pick activity

14. A workflow is just another name for a business process.
  
  - True
  - False

**Answer** - False

15. What extra information does a Partner Link provide compared with a Partner Link type? 
	
	- port type
	- role names
	- role played by each party
	- It does not provide any additional information. A Partner Link is merely an instance of a Partner Link type
	
**Answer** - role played by each party

16. Which description best fits "Static deployment time binding" of a service to a BPEL process?

  - Process model has explicit endpoints assigned.
	- Process model does not have explicit endpoints assigned but end-points are defined when the process is deployed to the workflow management system.
	- Criteria defined on the partnerLink that an end-point must have in a registry
	- Copying an endpoint variable from an invocation or request.   
	
**Answer** - Process model does not have explicit endpoints assigned but end-points are defined when the process is deployed to the workflow management system.

17. Which of the following is NOT a structured activity?
	
	- Sequence
	- Flow
	- If
	- While
	- Pick
	- All the above are structured activities
	
**Answer** - All the above are structured activities

18. Which of the following statement is NOT true. In a BPEL flow activity
	
	- A link can have multiple target activities
	- A target activity can be linked to multiple source activities
	- A source activity can be linked to multiple target activities
	- A link used in a while activity cannot reference activities outside that while activity 
	
**Answer** - A link can have multiple target activities

19. Which of the following things is true with respect to Correlation Sets (there may be more than one true answer)
	
	- Correlation sets are used to match a message with an instance of a process.
	- Compound business data is used as key, e.g. (customerID, orderNo)
	- Keys are automatically generated by the system and referenced in the messages 
	- If a correlation set is not match the process will fail 

**Answer** - 
  - Correlation sets are used to match a message with an instance of a process.
	- Keys are automatically generated by the system and referenced in the messages 
