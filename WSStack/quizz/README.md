## WS Stack and WSDL

1. A WSDL document can contain: 

  - Only abstract interface definitions
  - Only concrete implementation definitions
  - Can have both either abstract and concrete definitions, or both
  - Abstract and concrete definitions but not both
  
**Answer** - A WSDL document can contain both the abstract (interface) and concrete definition. The abstract definition describes the data structures, the messages and the port types. The port types define the operations (methods) that the client can access.

2. A target namespace refers to 
  
  - A namespace imported from some externally defined target.
	- Is the same thing as a default namespce.
	- Is a namespace used to validate an XML instance.
	- Is just an arbitrary name you can assign to any namespace.
	
**Answer** - The target namespace is used to validate the XML document. 

3. How would you define the minimum length user-defined type "phonenumber" derived from string.

  - <xsd:minInclusive value="4"/>
	- <xsd:minLength ="4"/>
	- <xsd:minLength value="4"/>
	- <xsd:phonenumber.length ="4"/>

**Answer** - <xsd:minLength value="4"/>, where the value attribute is 4. Because it is a user defined type, it follows the convention <xsd:facet value= "value"/>.

4. Mark all of the following that are WSDL Messages Exchange Patterns (MEPs)?

  - Push-Pull
  - Solicit-Response
  - Client Server
  - One way
  - Request-Response

**Answer** - Solicit-Response, Client Server, One Way and Request-Response are message exchange patterns. The one that is missing here is Notification, where the server sends a one way message to the clients.

5. Match the following element to either an abstract or concrete part of a WSDL 1.1 definition.
	
  - <operation>
  - <port>
  - <binding>
  - <types>
  - <service> 
  
**Answer**

  - <operation> - **Abstract (Interface) Part**
  - <port> - **Concrete Part** - The port type is in the abstract part.
  - <binding> - **Concrete Part** - The binding binds to the end point.
  - <types> - **Abstract (Interface) Part** - The types that the messages accept.
  - <service>  - **Concrete Part** - The operation from the interface connects to the service part.
  
6. Match the level of the Web service stack with the Web service standard.

  - WSDL
	- SOAP
	- BPEL (BPEL4WS)
	- WS-Security
	- HTTP
	- UDDI
	
**Answer** - 

  - WSDL - Description
	- SOAP - Messaging
	- BPEL (BPEL4WS) - Business Process
	- WS-Security - Quality of Service
	- HTTP - Transport
	- UDDI - Discovery
	
7. In WSDL, a one-way MEP is define with an operation that has: 

  - One output message
  - An input and and output message
  - One input message
  - The is no restriction on the types of message in an operation. The operation itself has an attribute MEP = "one_way"
  
**Answer** - One Way Message Exchange Pattern refers to a client sending a message to the server. In the WSDL the <operation> section it will specify a <input> message. 

A notification is a one way message sent from the server, it will contain only an <output> message.

8. The default type of an element in the form <xsd:element name=“elementName” type=“elementType”/> is:

  - string
	- boolean
	- integer
	- undefined
	
**Answer** - The default type unless otherwise specified is a string.

9. The maximum number of times the element <xsd:element name=“Assess_item”/> can occur within its parent is: 

  - Zero
	- One
	- Two
	- An unlimited number of times
	
**Answer** - The maximum number of times the element can occur within its parent is once.

10. WSDL is primarily a standard for Web Service:

  - Messaging
	- Description
	- Discovery
	- Deployment
	
**Answer** - The purpose of a WSDL is a description language. It is used to describe a service to the outside world.

11. Which of the following declares a default namespace?
	
	- xmlns:target="http://www.swin.edu.au/HIT8325"
	- xmlns:default="http://www.swin.edu.au/HIT8325"
	- xmlns="http://www.swin.edu.au/HIT8325"
	- None of the above

**Answer** - The default namespace is defined with the "xmlns" tag, any subsequent namespace has "xmlns:xsd" or whichever other extended name.

12. Which of the following is the most correct statement. A complex type can use a base type by:
	
	- extending it with extra attributes or content
	- restricting value ranges of the base type
	- extending or restricting the base type
	- None of the above. Only simple types can be derived from base types

**Answer** - extending or restricting the base type, it can be built from elements and/or attributes.

13. Which of the following statements is NOT true

  - XML Schema is a technology for validation of XML documents developed by the W3C
  - Both DTDs and XMLSchema support data types so XML data is accurately defined and specified in a document
  - XMLSchema allows greater flexibility in definition of a document type than DTDs
  - XML Schema is used to define web service standards

**Answer** - Both DTDs and XMLSchema support data types so XML data is accurately defined and specified in a document. DTD's do not support data types.
