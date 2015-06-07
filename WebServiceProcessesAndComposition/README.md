# Introduction to Web Service Processes and Composition

A **process** is a sequence of steps that is initiated by events, transforms the input and produces a specific output.

A **business process** is a set of logically related tasks to perform to achieve a **well defined business outcome**. It implies a horizontal view of an organisation and looks at the activities designed to produce an output for a customer or market. The achieved results can be defined in the context of the activities from the business process.

In short hand, it is a group of tasks performed to achieve a business outcome.

## Process Characteristics

- Contains **definitions** and **instances**.
- Contains **conditions triggering its initiation** for each new instance and defined outputs at its completion.
- Involves **formal** or **informal** interactions between participants.
- Contains **decision points**. Decisions made in regard to allocation of processing capacity.
- Usually **dynamic** and **long running**.
- Contains automated activities and workflow management.

## Types of Processes

There are many types of processess which can possess different characteristics depending on the need.

**Knowledge Workers** are people who are generally involved in the process (engineers, lawyers, consultants), which will require the process to be more adaptive.

There are more complex processes that are supported by **Adaptive Case Management (ACM)** and **Business Process Management (BPM)**

## Computerised Workflows

Applications can be used to implement the activities, processes and resouces in a workflow. It can also mediate the **data**, **message and communications**, **control and encapsulate** the workflow. Using an application to control the process requires the tracking of the **process instance state**.

## Activity Centric Workflow

An activity centric workflow uses a flowchart to track the activities.

### Coordination

- Orchestration - Describes how web services can interact with each other at the message level. This includes the business logic and execution order of the interactions from the perspective of a single endpoint.
- Choreography - Associated with globally visible (public) message exchanges, interaction rules and agreements that occur between multiple business endpoints. It tracks the messages that may involve multiple sources.

The difference being that the choreography view provides a higher level view of the process.

### Process Orientated Workflows

Are workflows that are used to **automate processes** where the structure is well defined and stable over a length of time. It can depict aspects of the business process (activities), decision points and rules. A well defined process is a process that doesn't really change much.

### Business Process Execution Language (BPEL) and Choreography Description Language (WS-CDL)

BPEL is a service composition (**orchestration**) language that facilitates the modeling and execution of **business processes** based on web services. It takes the view of a single participant and has wide spread support.

CDL is a language used to describe multi-party, peer to peer collaborations. It is not an execution language and is in fact a language that provides constraints and ordering on the system. It can be used to generate code skeletons, monitoring interactions, however it is not a widely adopted language specification.

### Process Orchestration - Activity Centric Process

Activity centric processes control the flow of execution

- Respond to messages and events.
- Sequences invocations.
- Are conditional and repeated.
- Handles errors.

Data Flow
- Messages are transformed as they pass through the composite.
- Stores the data temporarily.
- Invokes data services.

## Flow Model

Flow Models are used for the specification of complex service interactions. 

The flow model describes how the activities are combined and how the steps are executed. It also defines the data that is sent between the steps and the decisions performed.

There can also be **transition conditions** that define the constraints between the paths for each decision. 
