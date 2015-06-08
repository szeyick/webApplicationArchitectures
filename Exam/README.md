## Practice Exam Questions -

1. Describe how Enterprise Application Integration is facilitated by Web Service technology -

Enterprise applications, especially cross enterprise applications like a supply chain application requires communication between multiple corporations. Web service technology uses XML based communication for enterprises to talk to each other irrespective of the application languages.

Aside from the XML based interfaces, the transport message protocols use HTTP, which because it is a web technology is not going to blocked by firewalls.

2. Briefly Describe 4 types of services that might be aggregated into a supply chain application

- Payment Service
- Order Fulfillment
- Inventory Service
- Shipping Service

3. Explain the difference between a functional and non-functional property, given an example of each.

A functional property is a property that that adds to the functioning of the system, this can be a feature or a requirement such as a payment service. It is something that the system is supposed to do.

A non-functional property is a property of the system that does not add to its behaviour, things like performance, QoS, metrics would be a non-functional property. They are requirements that define part of the system but are not part of the functionality of the system.

4. What is the main purpose of a enterprise service bus?

The main purpose of a ESB is to combine bits and pieces of middleware into a single package. It manages the deployment and integration issues without the developer having to get into the nitty gritty. It manages behavhiour between different services. 

5. What is a business supply chain? What are its main parts

A business supply chain is the end to end process of how a business provides things to a end user.

The main parts of a supply chain are - procurement, transformation (material into final products) and distribution.

6. What is meant by the term service orientated architecture?

A service-oriented architecture (SOA) is an architectural pattern in computer software design in which application components provide services to other components via a communications protocol, typically over a network. It is a high level view of a system, where it provides limited details but covers the messages that are exchanged across each service.

7. What is the difference between web services and SOA?

Web Services is the application and SOA is the high level architectural view of the system.

8. What is the difference between stateful and stateless web service?

Stateful web service is a web service that maintains state, that is passed between the client and the service. It means that multiple invocations of a service may yield different results. A stateful web service would be a shopping web service, whereas the state would be the shopping cart that needs to be maintained each time the client adds an item to buy.

Stateless web service is a web service that does not bother to maintain state. This means that each time the service is invoked, it is treated as if it was started from scratch. A service that is stateless would be a simple fetch application such as retrieving weather or sports scores, the only data transferred is the requested data.

9. Explain how RPC and message styles of interaction differ -

RPC or remote procedure call requires the invocation of a method on the other side, or the client. The client is required to know about which method it is to call and it remains tightly coupled as cahnges in the service requires changes in the client.

Message style interaction involve the transmission of messages (usually XML format) from a client to the service. It is more robust, especially if it is a WS* based service as the middleware will deconstruct the document to find the correct service to invoke. Furthermore, with message style, the message payload can contain additional data which can be used or ignored by the web service.

10. Explain what is meant by the term choreographic langauge - 

A choreographic language would be a langauge that describes a high level view of the communications between web services. It is different to that of a orchestration language.

11. List 4 Advantages of Using Middlware -

- Less integration.
- Message transfer is managed by the middlware
- Easier to plug in applications whos implementation is written in different langauges.
- Security
- Autocode generation
- Message Transformation

12. List 4 Functions of Message Orientated Middleware (MoM)

- Message Transformation
- Message Transportation
- Business Rules Processing
- Events and Alerts
- Naming Services

13. What is a enterprise integration pattern? What type of architectural styles use these patterns?

Are a set of design patterns for use when integrating enterprise applications. It can be used with open source ESB's.

Example Patterns Include -

Integration Styles
Messaging Systems
Messaging Construction
Message Routing
Message Transformation
Messaging Endpoints
System Management

The types of pattern that use it are message based, event driven architectures.

14. List 2 advantages of RESTful approach compared to WS*

- Simpler to implement - Data is sent through using HTTP CRUD commands only and references processes through unique URI.
- No middleware required, as the client and service talk directly to each other.
- Data can be represented in multiple forms, just change the MIME-type.
- Stateless
- Fast Caching

15. List 2 advantages of WS* Service compared to RESTful

- Code skeleton generation through middleware, easier to integrate.
- More secure
- Standard protocols, SOAP and HTTP transport.
- Using a WS* middleware removes alot of the integration difficulty as it is managed by the middleware.

16. Explain how the 4 main HTTP verbs are used in RESTful approaches

- GET - Retrieve data from a service
- PUT - Update data to a service
- POST - Create a new process on the service.
- DELETE - Remove data from a service.

17. Why are RESTful/Resource based architecture claimed to be more scalable than WS* do you agree?

- Fast caching
- Highly scalable because it is stateless
- Late binding/linked services, client does not need to know all links in advance can be changed on the fly, so it is loose coupled.

18. What is pub/sub overlay network, describe the process which a subscriber receives information.

Publisher/Subscriber pattern, it is where a publisher pushes information into a message queue and the subscriber receives information from it. Another use would be for a publisher to push the information to the silo which the subscriber picks from.

19. Briefly describe the 3 styles of event processing in EDA -

- Simple Event Processing
- Complex Event Processing
- Stream Event Processing

20. What is a complex event -

A complex event is an event that is created/triggered by a series of other events, it is an aggregation of several events that causes a complex event to be triggered. Meaning that "if I these events come, then it is a other event"

21. What is JMS? What is the two communication models it supports -

JMS is Java Messaging Service, it is a means of which messages are transported between services. It supports Event Driven Communication Models and Publish Subscribe communcation models.

22. What are key ESB capabilities -

- Message transformation.
- Message transport.
- Service Integration.
- Fault and Error Handling.

23. What are two differences between XML Schemas and DTD's

24. What is the purpose of a XML namespace?

It provides a dictionary of verbs that can be used and understood by the XML schema.

25. Define a simple schema datatype called last name, whos max num characters is 40

```
<lastName>
  <maxLength value="40"/>
</lastName>
```

26. Define a XML Schema complex data type called PersonName that stores the name.

```
<PersonName>
  <firstName>
  <middleName>
  <lastName>
</PersonName>
```

27. What is the function of the import element in XML Schema?

The import element is used to identify additional XML documents that might be needed to add to the current schema. It contains reference links to other schemas.

28. What is the purpose of SOAP? Explain its major features or elements

SOAP is a messaging protocol that is used in WS*. Its major feature is that it uses XML to transport data across web services. Elements include, name spaces, data types, and all that stuff.

29. How is the SOAP mesage structured?

A SOAP message is called an envelope, it contains two parts, a <header> and <body>. The body is the mandatory part that contains the message payload. The header can contain information to intemediary nodes that can be added to validate or verify data before it eventually reaches the intended receiver.

30. How is modularity achieved in SOAP?



31. How is extensibility achieved in SOAP?

32. Why does a service need to be described?

Because otherwise external clients will not know where the service is and what to provide to it in terms of data or arguments.

33. In general, what aspects of a service need to be desribed and understood by consumers? Which standards are used to describe these aspects.

WSDL, the interface needs to be described, and message types to be put. Service.xml can be used to describe the service.

34. Outline the structure of WSDL documents and explain the purpose

- portType
- operations
- messageTypes
- messages

35. WSDL MEP, how can you tell which MEP is being used.

- Request/Response
- Notify
- One Way
- Solict/Response

You can tell which one is used based on the <message> tag and the order of the <input> and <output> elements.

36. Explain how a web service interface is linked to an implementation

The implemtantion and the abstraction is linked, by the portType is linked to the port, the messages are all linked and stuff like that.

37. Develop a WSDL description for a flight service

38. What is the difference between business process and workflow

- Business process is the description of a business in a horizontal manner that outlines its goals in a way
- A work flow is a the order of which a process is done.

39. What is HATEOAS, how is it used to implement a RESTful architecture

It is a WS* technology to implement RESTful architecture. It uses links sent back by the service to figure out what the next step or action is to take. It is client driven, rather than service driven.

40. How could progress of a process be tracked in a resource based service composition?

It can be tracked by the return messages and links. By updating the message return you can see where it is up to.

41. Explain why event driven processes can be readily adapted?

Because client and services do not need to know specifically about each other, they operate on a fire and forget model.

42. What needs to be changed if the control flow of RESTful process needs to be altered.

The return links from the service message.

43. Explain what is meant by a BPEL abstract process

44. List the 7 main sections in a BPEL process definition and briefly describe their function

45. What is a partnerlinktype in BPEL

A partnerlinktype describes the communication models between the sender and recipient.

46. How many roles does an asynchronous partner link have 

47. What is a BPEL binding scheme -

48. Describe how parallel activities are implemented in BPEL

Through the flow element, the flow element allows activities to be executed in parallel.

49. How does BPEl create process instances? How is one process instance distinguished from another

Through the receive or pick activity. Instances are distinguished from each other by generated keys that map the instances and differentiate them.

50. What code is required to create an instance of a BPEL process -

createInstance="yes"

51. What is difference between compentation handler and fault handler?

52. Which architectural style is more suitable for knowledge intensive process? Explain your answer

53. What are policies and why are they important to WS applications?

Policies define how and stuff, they are important because it defines the governance of how to access a service.

54. List two common policies for web services.

55. Describe and explain the structure of a WS-Policy Document

56. How are policies enforced.

57. Describe four levels of the message delivery assurance.
