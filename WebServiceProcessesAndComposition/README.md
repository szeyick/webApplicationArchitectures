# Introduction to Web Service Processes and Composition

A **process** is a sequence of steps that is initiated by events, transforms the input and produces a specific output.

A **business process** is a set of logically related tasks to perform to achieve a **well defined business outcome**. It implies a horizontal view of an organisation and looks at the activities designed to produce an output for a customer or market. The achieved results can be defined in the context of the activities from the business process.

In other words, a business process provides a horizontal view of an organisation looking at its process as a set of activities.

The process defines the results in activites, the relationships between them and how it interacts with other processes.

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

A knowledge intensive process provides a standard definition that is task orientated where decision are made. This is different compared to a manufacturing process where the complete definition is required at the start and is goal orientated.

## Computerised Workflows

Applications can be used to implement the activities, processes and resouces in a workflow. It can also mediate the **data**, **message and communications**, **control and encapsulate** the workflow. Using an application to control the process requires the tracking of the **process instance state**.

We can use a computerised workflow to implement activites, processes and updates. It is used to sketch out the control of flow and data through a business process. Progress is measured by tracking the current process state.

## Activity Centric Workflow

An activity centric workflow uses a flowchart to track the activities.

### Coordination

- Orchestration - Describes how web services can interact with each other at the message level. This includes the business logic and execution order of the interactions from the perspective of a single endpoint. It is an activity centric way to describe how web services interact with each other.

- Choreography - Associated with globally visible (public) message exchanges, interaction rules and agreements that occur between multiple business endpoints. It tracks the messages that may involve multiple sources (services).

The difference being that the choreography view provides a higher level view of the process.

### Process Orientated Workflows

Are workflows that are used to **automate processes** where the structure is well defined and stable over a length of time. It can depict aspects of the business process (activities), decision points and rules. A well defined process is a process that doesn't really change much.

It is a activity centric workflow used with well known processes that have clearly defined processes that don't really change.

### Business Process Execution Language (BPEL) and Choreography Description Language (WS-CDL)

BPEL is a service composition (**orchestration**) language that facilitates the modeling and execution of **business processes** based on web services. It takes the view of a single participant and has wide spread support.

It is an execution language that helps with the modelling and execution of a process. It is activity centric and takes the view of a single participant passing messages in and out.

CDL (Choreography Description Language) is a language used to describe multi-party, peer to peer collaborations. It is not an execution language and is in fact a language that provides constraints and ordering on the system. It can be used to generate code skeletons, monitoring interactions, however it is not a widely adopted language specification.

CDL is a non-execution language that specifies the ordering of activites and constraints on global messages. Because it is a non-execution language, it is used to generate code skeletons and monitor interactions on a global scale.

### Process Orchestration - Activity Centric Process

BPEL is a process orchestration language. With it we can draw up control execution flow, describe how to repond to messages and events along with errors and conditional flows (if statements).

In a BPEL diagram, data flowing from one activity to another is transformed from one format to another. It also stores data and invokes services (ESB).

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

Flow Models are used for the describing of complex service interactions. It shows which activites are executed, if they are combined and also the order.

The flow model describes how the activities are combined and how the steps are executed. It also defines the data that is sent between the steps and the decisions performed.

## Event Driven Process - Event Driven Architecture

Control flow is described by "Event Process Chains", it is a diagram that graphs the order of events and functions, much like a normal state diagram. It is another non-executable process language.

## Service Orchestration

BPEL or Orchestration (Activity Centric) differs from Java as control flow is based on messages being transferred between activities. In Java the transfer between activities or methods is done through the sending of objects. Furthermore BPEL is usually performed asynchronously whereas control flow in Java can tend to be synchronous.

## BPMN - Business Process Modelling Notation -

Is a non-executable modelling notation for drawing and defining a business process.

## Artifact Centric Workflow - HATEOAS

An artifact can be defined as a document (XML) or thing. It is a state based workflow and process through the system is tracked by the changing or update of the document that is being passed through the process.

It is a RESTful process, where resource update is performed with HTTP (CRUD) as with normal REST process invocations, but the response will also contain the next steps (links) in the process. The response contains information or links to the location of the next steps in the process that can be re-executed by the server. The process is client driven from the links provided by the server.
