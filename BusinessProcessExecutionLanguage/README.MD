# Introduction to BPEL

BPEL is a standard based on SOAP WS*, therefore it is used to integrate SOAP services to support a business process.

Anything involving multiple activities can be considered as a business process, well services coupled together.

A business process is a set of related tasks that are coupled together to achieve a business outcome.

Data dependant behaviour is the relationship between activities.

Distributed business processes can be across multiple sites.

## Activity Centric Business Process Concepts

- A flow model describes the order between activities or tasks.
- Data/Messages will be passed between the activities as they are executed.

## Business Process Modelling

It is understanding the activites that are involved in a process, when they start, when they end and the specific activities that dictate the order in which they are executed.

Modelling can be done in many different ways 

- UML Activity Diagrams - Provides a high level activity based view of the process.
- BPMN - Non-exectuable Business Process Modelling Notation, a notation that is standardised by OMG. Provides comprehensive details.
- BPEL - Is executable.

Other notations that can be used -
- EPC - Event Process Chains
- CDL - Choreography Description Language

## UML Activity Diagrams

- The activity diagram is essentially a UML flowchart to describe the control from activity to activity.
- It can be used to forward or reverse engineer a system.
- The black lines in the diagram describe concurrent activities that need to be completed before it can proceed to the following activity or finish state.
 
### Key Concepts

- Activity State - An executable part of the diagram (non-atomic, can be combined).
- Action State - An executable part of the diagram (atomic)
- Transition - Shows the passing of control from one activity/action to another.
- Branching - Takes a boolean expression to branch to different activity/action states. The outcome of the path is detailed.
- Forking/Joining - Handles concurrent activity/action state execution, shows that two tasks that need to finish before the next activity commences.
- Swim Lane - It groups activities together logically, used to categorise parts of the activity diagram to outline what each section does.

## Business Process Development 

- Top Down - creates the business model first, then the process (BPEL) followed by the service.
- Bottom Up - create the service first, then the process (BPEL) followed by the business model

## BPEL

WSDL defined Web services have a stateless interaction model, which is sometimes insufficient when describing a business process. This is where BPEL comes in, it provides a more detailed view of the business process by introducing state, long running interactions that are designed to work with SOA.

WSDL and BPEL are used in conjuction to define a business process. The language forms are both placed into a process engine that is used by the client to access the web service. Each client accesses a different instance of the process.

### BPEL Process Structure

It is a XML document.

- Partner Links - Functions almost as imports that define the other processes that you may use within the current process. It establishes partner relationships by specifying the **roles of each party**. This is defined in the **BPEL Document**.

- Correlation Sets - Identifies what kind of activities/data from the client links to a particular instance.

- Partner Link Type - Describes the communication relationship between two partners by defining the **role** that each partner plays in an interaction and the **port types**. It links the defined role with the port types defined in the WSDL document.
 
### Partner Link to Partner Link Type

It seems very similar to how we associated WSDL service end points. 

The important parts here are the port type on both sides, and the partner link that defines the roles that each service plays.

A benefit of multiple roles to the same service is that you can use it as a load balancer.

- The parterLink contains reference to the parterLinkType along with the roles played. 
- The parterLink type contains the the roles played but also the portType that it is linked to. This port type (in WSDL), is then linked to the operation defined in the WSDL (The method to call).

So the parter link and partner link type sit in the BPEL side, and the port type and operation site in the WSDL side.

BPEL Document.
```
<parterLinks>
  <partnerLink name="Purchasing" parterLinkType="PurchaseOrderPLT" myRole="PurchaseService"/>
  <partnerLink name="CreditChecker" parterLinkType="CreditCheckPLT" myRole="CreditRequester" parterRole="CreditChecker"/>
</partnerLinks>
```

BPEL Document Parter Link Type
```
<parterLinkType name="PurchaseOrderPLT">
  <role name="PurchaseService">
    <portType name="PurchaseOrderPortType>
  </role>
</partnerLinkType>
<parterLinkType name="CreditCheckPLT">
  <role name="CreditRequester">
    <portType name="CreditCheckPortType>
  </role>
    <role name="CreditChecker">
    <portType name="CreditCheckCallbackPortType>
  </role>
</partnerLinkType>
```

WSDL Port Type
```
<portType name="PurchaseOrderPortType">
  <operation name="SendPurchase">
  ...
  </operation>
</portType>
```

### Binding Partners to Endpoints

There are four binding schemes that are possible to bind services.

- Static Design Time Binding - Explicit Endpoints (Static)
- Static Deployment Time Binding - Process end points are defined when process is deployed.
- Dynamic Binding Using Lookup - Look for an endpoint from a registry.
- Dynamic Binding with Passed in Endpoints - Copying the endpoint from a invocation/request.

### Basic Activities (I/O)

There are three basic activities.

- \<receive\> - Waiting for an operation from an external client.
- \<invoke\> - A do something or invocation of service.
- \<reply\> - A response to the client.

These tags are within the BPEL process that are the links between the services.

The above are processed asynchronously, if you want a synchronous process, the \<recieve\> \<reply\> are coupled together in the flow. 

### Variables and Assigning

Messages pass the data around between processes. We can use variables to hold data for us within the message. These are represented as a \<variable\> tag. Furthermore we can use the \<assign\> tag to copy data into variables.

The variable is used to maintain state, it can include message content and any intermediate data that can be used to send data around to various activities.

The variables follow the following format

```
<variables>
  <variable name="PO" messageType="lns:POMessage"/>
</variables>
```

The message type in the variable links to the WSDL messages types defined.

```
<message name="POMessage">
  <part name="customerInfo" type="sns:customerInfo"/>
</message>
```

Extracting can be done using XPath queries within the BPEL document in the assign tag.

```
<assign>
  <copy>
    <from variable="PO" part="customerInfo" query="/something/text()"/>
    <to variable="AnotherDefinedVariable part="variablePartName query="/something/text()"/>
  </copy>
</assign>
```
- BPEL Assign - The element used to copy data between variables. Data can be copied into variables through XPath, copy from to variables.
