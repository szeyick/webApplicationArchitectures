# Introduction to BPEL

BPEL is a standard based on SOAP WS*, therefore it is used to integrate SOAP services to support a business process.

Anything involving multiple activities can be considered as a business process, well services coupled together.

A business process is a set of decisions that reach an outcome. 

Data dependant behaviour is the relationship between activities.

Distributed business processes can be across multiple sites.

## Activity Centric Business Process Concepts

- A flow model describes the order between activities or tasks.
- Data/Messages will be passed between the activities as they are executed.

## Business Process Modelling

It is understanding the activites that are involved in a process, when they start, when they end and the specific activities that dictate the order in which they are executed.

Modelling can be done in many different ways 

- UML Activity Diagrams - Provides a high level activity based view of the process.
- BPMN - Business Process Modelling Notation, a notation that is standardised by OMG. Provides comprehensive details.
- BPEL - Is executable.

Other notations that can be used -
- EPC - Event Process Chains
- CDL - Choreography Description Language

## UML Activity Diagrams

- The activity diagram is essentially a flowchart to describe the control from activity to activity.
- It can be used to forward or reverse engineer a system.
- The black lines in the diagram describe concurrent activities that need to be completed before it can proceed to the following activity or finish state.

### Key Concepts

- Activities - An action or atomic activity, it is an executable component in the flow.
- Activity State - A composition of actions
- Transitions - The arrows between the activities. It defines the orders between the activities.
- Branching - The If/Else
- Forking - Parallel/Split tasks that can be done concurrently. It represents the start/end of a concurrent activity.
- Swim Lane - A grouping of activities performed by an individual stakeholder, much like swim lanes defined in Agile development. 

## BPEL

WSDL defined Web services have a stateless interaction model, which is sometimes insufficient when describing a business process. This is where BPEL comes in, it provides a more detailed view of the business process by introducing state, long running interactions that are designed to work with SOA.

WSDL and BPEL are used in conjuction to define a business process. The language forms are both placed into a process engine that is used by the client to access the web service. Each client accesses a different instance of the process.

### BPEL Process Structure

It is a XML document.

- Partner Links - Functions almost as imports that define the other processes that you may use within the current process. It establishes partner realationships by specifying the **roles of each party**. This is defined in the **BPEL Document**.
- Correlation Sets - Identifies what kind of activities/data from the client links to a particular instance.
- Partner Link Type - Describes the communication relationship between two partners by defining the **role** that each partner plays in an interaction and the **port types**. This is defined in the **WSDL Document**.

### Partner Link to Partner Link Type

It seems very similar to how we associated WSDL service end points. 

The important parts here are the port type on both sides, and the partner link that defines the roles that each service plays.

A benefit of multiple roles to the same service is that you can use it as a load balancer.

### Binding Partners to Endpoints

There are four binding schemes that are possible to bind services.

### Basic Activities (I/O)

There are three basic activities.

- <receive> - Waiting for an operation from an external client.
- <invoke> - A do something or invocation of service.
- <reply> - A response to the client.

These tags are within the BPEL process that are the links between the services.

### Variables

Messages pass the data around between processes. We can use variables to hold data for us within the message. These are represented as a <variable> tag. Furthermore we can use the <assign> tag to copy data into variables.
