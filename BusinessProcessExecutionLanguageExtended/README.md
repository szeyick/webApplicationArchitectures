# BPEL Part 2

The way that BPEL works is through XML. An example of this is through the purchase ordering process -

Case 1 -

A **client (partner)** placing a purchase order and **supplier (process)** who tries to fulfill the clients request. The supplier communicates with the **credit service (partner)**, **billing service (partner)** and **inventory service (partner)** to complete the clients request. An invoice is generated from this and returned to the client.

**BEPL purchase order process**

The way that the communication is handled is through a series of XML documents, where the relationships between the client, process and partners is defined. In addition, we can also define **data structures** in XML that will carry the state data across the process to each partner when required.

## Structured Activities -

These describe how a business process is created by composing the basic activities it performs into structures that express control patterns and coordination of message exchanges.

It allows -

- To specify which activites should be run **sequentially** (\<sequence\>) or in parallel (\<flow\>).
- To branch activities (\<if\>).
- To specify a alternate path based on an event (\<pick\>).
- To define iterations (\<while\>, \<repeatUntil\>, \<forEach\>).
- Associate an activity with its own local variable and handlers (\<scope\>).

### Sequence -

A sequence defines a sequential series of steps through a process. These must be executed in order.

```
<sequence S>
  <A/>
  <B/>
  <C/>
</sequence>
  
```

### Flow -

A flow defines activities that can be executed in parallel. Within a flow activity, we have **\<links\>** that synchronise a **source** activity to a **target** activity. For each link in a flow, it must have exactly **one source activity and one target activity**.

Flows also have **transitional** conditions that are evaluated when a source completes. These can then be followed by **join conditions** that determine whether to move to the next activity.

```
<flow F>
  <links>1,2,3,...6</links>
  <A>
    <sources>
      <source 1/>
      <source 2/>
      <source 3/>
    </sources>
  </A>
  <B>
    <targets>
      <target 1/>
    </targets>
    <sources>
      <source 4/>
    </sources>
  </B>
  ....
</flow>
```

From an XML structure, there is no difference between the sequence and flow, just that they perform their tasks in sequential order or in parallel.

### Conditional Selection (if)

This activity consists of an ordered list of conditional branches made up of <if> and/or <else>, <elseif> (optional). These function like conditional statements as with any other programming langauge.

```
<if standard-attributes>
  <condition expressLanguage="anyURI"?>bool-expr</condition>
    ** activity **
  <elseif>
    <condition expressLanguage="anyURI"?>bool-expr</condition>
    ** activity **
  </elseif>
  <else>
    ** activity **
  </else>
</if>
```

### Iteration (while & repeatUntil)

Used the same as with standard programming langauges to repetitively execute an activity.

```
<while>
  <condition>$orderDetails &gt; 100</condition>
    ** activity **
</while>
```

The \<repeatUntil\> works the same, however is similar to a **do;while** condition statement, as it will execute then evaluate, meaning that the loop will at least execute once.

There is also a <forEach> activity that executes exactly **N + 1** times, where processing within it can be executed in serial or parallel. The activities contained within the <forEach> loop must be within a <scope> element. Further to that, an optional <completeionCondition> can be added that will be evaluated whenever a <scope> activity is completed. This allows for early termination of the loop.

For normal termination of the loop, we define the values in the <startCounterValue> and <finalCounterValue> elements.

### Selecting Events (pick) -

This activity waits for exactly one event to occur from a set of events, then executes an activity based on the event. A pick is comprised of a set of branches, containing an event-activity pair.

A pick activity event comes in two forms -

- The <onMessage> is similar to a <receive> activity, as it waits for the receiving of an inbound message.
- The <onAlarm> is based on a timer event.

A pick activity **must** include at least one <onMessage>.

### Defining Context (scope, process)

A <scope> provides the context which influences the execution behaviour of the activities that is encloses. This can include, variables, partner links, events anything else that the activity needs to execute.

The difference between a scope and process is that a process is not an activity. In addition, a compensation handler cannot be added to a <process>

### Timed Activiies (wait)

We can delay an execution of an activity for a specified time with the \<wait\> element.

```
<sequence>
  <wait>
    <until>'2015-12-24T18:00+01:00'</until>
  </wait>
  <invoke>....</invoke>
</sequence>
```

### Error Handling (throw, rethrow, exit)

It can be used to throw an error or exception. The <throw> activity provides the name for the fault and data if required.

```
<throw xmlns:FLT="http://example.com/faults" faultName="FLT:OutOfStock"/>
```

We can use \<rethrow\> in fault handlers to rethrow a fault that they caught, but can only be used within a \<catch\> and \<catchAll\> element.

\<exit\> activity can be used to immediately end the process.

### Correlation Sets

To instantiate a new instance of an activity we can set the **createInstance** attribute to the the \<receive\> and \<pick\> activities. It defines the start points of the activity, meaning **the first message to arrive at this point creates the new instance**. Messages that arrive later **correlate** to the instance that was previously created.

Each process has **at least one** start activity, and it terminates when the last activity completes or an error is produced.

```
<sequence>
  <recieve partnerLink="Purchasing" portType="lns:PurchaseOrderPortType" operation="SendPurchase" variable="PO" createInstance="yes">
  
  </receive>
  ....
  <flow>
  ....
  </flow>
  <reply .... />
</sequence>
```

A correlation set defines a group of properties from an incoming message that allows us to associate it to a particular instance of a process. The generated key from the message properties, can be used to identify which instance the data belongs to even though the web service is designed to be stateless.

We can use this mechinism to create multiple correlation sets to uniquely identify processes that exist across multiple web services. 

### Handlers

Handlers provide a mechanism of reacting to particular events and are associated to a **scope**.

- **Event Handlers** - Allows the scope to reach to event messages (i.e \<pick\>) or alarms (timers).
- **Fault Handlers** - Handles faults that are thrown within their scope.
- **Compensation Handlers** - Defines how to undo a completed activity.
- **Termination Handler** - Control a force termination in a scope.

#### Event Handlers

There are two types of event handlers **inbound message** and **alarms**. These only exist for the duration of their scope and cannot create new process instances.

```
<process name="orderCar">
  <eventHandlers>
    <onEvent partnerLink="buyer" portType="ns:purchasing" operation="cancelOrder" messageType="ns:cancelOrderMessage" variable="cancelDetails">
    <scope>
      <exit/>
    </scope>
    </onEvent>
  </eventHandlers>
</process>
```

The above code example details how a handler will stop a process instance when it receives a **cancel order** event occurs.

#### Fault Handlers

It can be associated to a scope, process or invoke. If we reach a fault handler it means that the normal execution can no longer be completed and we need to stop all additional work in the scope. Within the handler, we can define what to do when a fault has been thrown.

For fault handling, when it occurs it means that the scope has failed and will require a scope (not neccessarily the one that threw it) to handle the fault. If no handler is defined in the current scope where the error has been thrown, it will flow down to the next scope.

```
<faultHandlers>
  <catch faultName="OrderNotComplete faultVariable="POFault">
    <reply partnerLink="Manufacturer" portType="PurchasePortType" operation="Purchase" variable="POFault" faultName="OrderNotComplete/>
  </catch>
  ....
  <catchAll/>
</faultHandlers>
```

The above code example details how a handler catches an error. It uses a \<reply\> message to return the fault to the manufacturer.

#### Compensation Handling

It can be used to undo a successfully completed activity within a scope. The \<compensateScope\> or \<compensate\> activity is used to define the scope of this behaviour, however it can only be defined within the FCT (Fault, Compensation, Termination) handlers.

```
<scope name="S1">
  <faultHandlers>
    <catchAll>
      <compensateScope target="S2".>
    </catchAll>
  </faultHandlers>
  <sequence>
    <scope name="S2">
      <compensationHandler>
      <!-- Undo Work -->
      </compensationHandler>
      <!-- Do some work -->
    </scope>
    <!-- Do some more work -->
    <!-- If a fault is thrown here, the results of S2 must be undone -->
</scope>
```

#### Termination Handler

It allows the scope to control its own termination. The \<exit\> activity **does not invoke the termination handler**. It executes before the fault handler executes. All other running work within the scope is also terminated. Structured activities are terminated, and the termination is propagated into their contained scopes.

After the scopes primary activity and all running event handler instances are stopped, the termination handler will run. It is useful for cleaning up the process and returning messages to the user.

```
<scope>
  <terminationHandler>
    <!-- Clean up resources in case a forced termination is invoked -->
  </terminationHandler>
  <sequence>
    <!-- Do Some Work -->
  </sequnce>
</scope>
```
