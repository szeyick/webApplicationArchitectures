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



