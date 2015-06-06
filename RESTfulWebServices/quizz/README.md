## RESTful Services Quizz

1. Defining specific services interface as in WSDL
  - Makes it more difficult to determine the functionality of a service 
	- Is more flexible than the REST approach
	- Makes it easier to change the service implementation
	- Is more tightly coupled than the REST approach 
	
**Answer** - WSDL defines the exposed interfaces that link to a web service. The document contains the in/out message types, and the interfaces that the concrete implementation is to implement. If the interface changes, especially for the message types, it will usually mean that the implementation will require changes also. 

REST on the other hand, the URI can change, but it does not affect the structure or content of the message being sent, therefore using WSDL with WS* is more tightly coupled that using REST.

2. Which of the following HTTP methods are IDEMPOTENT? (More than one answer may be correct)
  - GET - Retrieve the contents from a resource.
  - POST - Create a new resource.
  - PUT - Update a resource.
  - DELETE - Delete a resource.
  
**Answer** - Idempotent methods means that multiple invocations of the method with the same parameters will not alter the result. In this instance, GET, PUT and DELETE would be idempotent methods as invoking them over and over again will always return the same result. For PUT, it will update a resource with the same values, and with DELETE after it has deleted once, it will delete nothing but does not change the resource contents.

Multiple invocations of POST on the other hand will continue creating new resources with the same attributes.

3. Match the HTTP operation to its conventional purpose in REST/HTTP (GET, POST, DELETE, PUT)
	
  - Create a resource
  - Update a resource
  - Remove a resource
  - Retrieve information, possibly cached

**Answer** - 

  - Create a resource - POST
  - Update a resource - PUT
  - Remove a resource - DELETE
  - Retrieve information, possibly cached - GET
  
4. Match the following characteristics to either a 
  - a. RESTful approach
  - b. WS* approach 
	
  - Allows multiple representation of an interface
	- Is a 'resource' based approach
	- Has a few endpoints with many operations
	- Every thing is a URI
	- Has many endpoints with few operations
	- Explicitly handles security

**Answer**

  - Allows multiple representation of an interface - **REST**
	- Is a 'resource' based approach - **REST**
	- Has a few endpoints with many operations - **WS**
	- Everything is a URI - **REST** (All resources are referenced by URI)
	- Has many endpoints with few operations - **REST** (Few operations means the CRUD for REST)
	- Explicitly handles security - **WS**
	
5. A Resource-based / RESTful architectural is just another name for an Internet CRUD (Create, Read, Update, Delete) based application that uses HTTP verbs to do these operations.
  
  - True
  - False
  
**Answer** - False. RESTful architecture uses HTTP verbs (GET, PUT, POST, DELETE) to perform operations on the service.

6. REST is 

  - A Web Service architectural style based on HTTP - Uses HTTP verbs to perform actions on operations.
  - A message pattern involving request and response - (WS* using request/response pattern)
  - A Web service standard - (WS* is the web service standard, the * refers to standards)
  - The architecture of the Internet

**Answer** - A web service architectural style based on HTTP. 

7. REST treats HTTP as a 
  - Transport protocol
	- Application protocol
	- Optional protocol
	- None of the above

**Answer** - REST treats HTTP as a application protocol. The message data and operations are sent using the CRUD verbs to the described URL. Furthermore, it can also use the HTTP to store required variables for the resource. 

WS* uses HTTP as a transport protocol, with SOAP being the container for the message.

8. A RESTful Web service achieves multiple different representations of a resource by

  - Including representation type information in a separate OPTION request
  - Specifying a MIME-type for each representation the resource can be delivered in
  - Including representation type information in a parameter of the GET
  - RESTful services cannot present multiple representations
  
**Answer** - REST resources can be anything (XML, audio, video etc), and the representation of the resource data can be specified within the URI as a Accept-Content type (MIME-Type). The type information is stored as an additional parameter in the URI.

9. Processes in Resource-based architecture typically: 
  - are defined in BPEL - (Mainly used in WS*)
  - under the control of a single controller service (The controller service is usually used in WS*)
	- have control decentralised across the client and resources 
	- not possible
	
**Answer** - Have control decentralised across the client and resources. REST has no middleware, so control should be shared between the client and resources by communicating through the URI.

10. Which of the following HTTP methods are SAFE (More than one answer may be correct)
  
  - DELETE
  - POST
  - GET
  - PUT
  
**Answer** - In REST, Safe methods are methods that when invoked multiple times will not change the state of the resource. In this instance GET will be the only REST method that returns the same result each time. POST creates a new resource each time, PUT updates a resource so it changes each time and DELETE will remove something from the resource.

11. Stateless communication can best be described as
  
  - The inability of an application to store state 
  - The ability of a server to cache requests from the client
  - The server not tracking the state of the client
  - The communication between the client and the server does not contain any representation of state

**Answer** - Stateless communication is where the service does not track the state of the client. In REST, services do not maintain the state unless it actually saves the data onto some back end file system.

12. The main advantage of use HTTP as a transport is that

  - There is no advantage in using HTTP 
  - HTTP can get through most firewalls as ports 80 or 8080 are usually left open for Web traffic
  - It is quicker than other protocols
  - HTTP cannot be used a transport protocol as it is an application protocol (Transport Protocol - WS*, Application Protocol - REST)
  
**Answer** - HTTP because it is a standard web protocol is usually exempt from most firewalls, this means that in many enterprise services, it can be used even through the corporate security.

13. What does REST stand for?

  - Remote Service Tranport
  - Resource Service Transfer
  - Remote Electronic State Transfer
  - Representational State Transfer
  
**Answer** - REST stands for Representational State Transfer.

14. What does the acronym POX in the Web service domain stands for .......

**Answer** - Plain Old XML.

15. Which is **not** a perceived advantage of REST

  - Easier to define complex workflows
  - Highly scalable
  - Process flow decisions can be determined by the client  
  - GET requests can be cached at the Caching Proxy or Reverse Proxy

**Answer** - Complex workflows is difficult to do in REST because you're limited to CRUD operations. This means that everything that the process can do is limited to PUT, PUSH, DELETE, GET. Complex work flows will require the service to be split up into smaller chunks. REST cannot be used to do multiple DELETEs on the same URI resource since the DELETE cannot be sure as to which process to operate on.
