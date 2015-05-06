# BPEL Part 2

The way that BPEL works is through XML. An example of this is through the purchase ordering process -

Case 1 -

A **client (partner)** placing a purchase order and **supplier (process)** who tries to fulfill the clients request. The supplier communicates with the **credit service (partner)**, **billing service (partner)** and **inventory service (partner)** to complete the clients request. An invoice is generated from this and returned to the client.

**BEPL purchase order process**

The way that the communication is handled is through a series of XML documents, where the relationships between the client, process and partners is defined. In addition, we can also define **data structures** in XML that will carry the state data across the process to each partner when required.

## Structured Activities -

These describe how a business process is created by composing the basic activities it performs into structures that express control patterns and coordination of message exchanges.

It allows -

- To specify which activites should be run **sequentially** (<sequence>) or in parallel (<flow>).
- To branch activities (<if>).
- To specify a alternate path based on an event (<pick>).
- To define iterations (<while>, <repeatUntil>, <forEach>).
- Associate an activity with its own local variable and handlers (<scope>).

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

A flow defines activities that can be executed in parallel. Within a flow activity, we have **<links>** that synchronise a **source** activity to a **target** activity. For each link in a flow, it must have exactly **one source activity and one target activity**.

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

### Conditional Selection (<if>)

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

### Iteration (<while> & <repeatUntil>)

Used the same as with standard programming langauges to repetitively execute an activity.

```
<while>
  <condition>$orderDetails &gt; 100</condition>
    ** activity **
</while>
```

The <repeatUntil> works the same, however is similar to a **do;while** condition statement, as it will execute then evaluate, meaning that the loop will at least execute once.

There is also a <forEach> activity that executes exactly **N + 1** times, where processing within it can be executed in serial or parallel. The activities contained within the <forEach> loop must be within a <scope> element. Further to that, an optional <completeionCondition> can be added that will be evaluated whenever a <scope> activity is completed. This allows for early termination of the loop.

For normal termination of the loop, we define the values in the <startCounterValue> and <finalCounterValue> elements.

### Selecting Events (<pick>) -

This activity waits for exactly one event to occur from a set of events, then executes an activity based on the event. A pick is comprised of a set of branches, containing an event-activity pair.

A pick activity event comes in two forms -

- The <onMessage> is similar to a <receive> activity, as it waits for the receiving of an inbound message.
- The <onAlarm> is based on a timer event.

A pick activity **must** include at least one <onMessage>.

### Defining Context (<scope>, <process>)

A <scope> provides the context which influences the execution behaviour of the activities that is encloses. This can include, variables, partner links, events anything else that the activity needs to execute.

The difference between a scope and process is that a process is not an activity. In addition, a compensation handler cannot be added to a <process>

### Timed Activiies (<wait>)

We can delay an execution of an activity for a specified time with the <wait> element.

```
<sequence>
  <wait>
    <until>'2015-12-24T18:00+01:00'</until>
  </wait>
  <invoke>....</invoke>
</sequence>
```

### Error Handling (<throw>, <rethrow>, <exit>)

It can be used to throw an error or exception. The <throw> activity provides the name for the fault and data if required.

```
<throw xmlns:FLT="http://example.com/faults" faultName="FLT:OutOfStock"/>
```

We can use <rethrow> in fault handlers to rethrow a fault that they caught, but can only be used within a <catch> and <catchAll> element.

<exit> activity can be used to immediately end the process.
