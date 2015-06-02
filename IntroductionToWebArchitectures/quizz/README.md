## Introduction to Web Services Quizz

### Questions -

1. The acronymn EAI stands for

  - Enterprise Application Interface
  - Enterprise Application Integration
  - E-Commerce Application Interface
  - None of the above

**Answer** - EAI stands for Enterprise Application Integration. It is a set of principles that define how to integrate a set of enterprise computer applications together. In the context of web services, it would be the definition of how to integrate a set of web services to create a complex web service.

2. Match each of the attributes with the type of requirement: Functional, Development-time quality, QoS

  - Reliability
  - Ability to perform a task
  - Performance
  - Modifiability

**Answer**
  - Reliability - QoS (Quality of Service) as reliability is a non-functional requirement of a system.
  - Ability to perform a task - Is a functional requirement, whether a system does a task or not.
  - Performance - QoS as performance is a non-functional requirement of a system.
  - Modifiability - Development Time Quality as it shows the impact of how easily a system can be modified during development.
  
3. In the context of distributed computing, the acronym MoM stands for

  - Management of Messages
  - Monitoring of Messages
  - Message-oriented Middleware
  - Message-oriented Mediation
  
**Answer** - MoM stands for Message Orientated Middleware. It is a means of services or clients communicating with each other through a message based middleware that acts as a mediator between the various services. This allows for clients and services to not know directly about each other as communication is managed by the middleware.

4 . SOA is an implementation of Web Services

  - True
  - False

**Answer** - SOA is an architecture style that defines how web services communicate with each other. It defines how a web service should be implemented, therefore it is not an implemtnation of web services. An implementation of Web Services is RESTful or WS* (Web Service Specification).

5. Which of the following is NOT a common property of Enterprise SOA

  - Asynchronous messaging 
  - Long-lived transactions
  - Strong coupling
  - Course-grained services
  
**Answer** - Strong coupling is not a common property of enterprise SOA. The objective of SOA is to reduce coupling through WSDL and SOAP. Enterprise SOA requires asynchronous messaging as it is expected to handle high loads, long lived transactions (stateful) and course grained services (complex services that require other services).
  
  There may be more than one correct answer to the following question.

6. Web services are usually

	- Fine grained
	- Synchronous
	- Loosely coupled
	- Can be stateful
	- Do not have non-functional properties

**Answer** - Web services are usually course grained (complex and communicate with other services), loosely coupled (do not depend on other services), stateful (maintains session data like shopping cart). They are not usually synchronous as waiting for responses is usually bad and will always have non-functional properties (QoS, Performance Metrics).

7. What is a key difference between RPC and a message-oriented Web architectural style?

  - RPC is synchronous
  - RPC uses domain specific methods
  - RPC can naturally implement solicit-notify interaction 
  - The is no difference. They are the same thing.
  
**Answer** - RPC is purely synchronous.

Message orientated architecture styles usually employ a "fire and forget" messaging system. This means that a message can be sent by a service or client without waiting for a response to continue processing. RPC and Message Orientated styles are not the same thing.

8. Which of the following is NOT a common architectural style for the Web

	- WS*
  - RPC
  - RESTful
  - Pipe and Filter
  
**Answer** - Pipe and Filter, the rest are all architectural and implementation styles for the web.

9. WS* and RESTful approaches to can be used to implement various Web architectural style. Which approach best supports the following styles? 

  - RPC
  - Resource-oriented
  - Message-oriented
  - Event-oriented

**Answer** 

  - RPC - WS*
  - Resource-oriented - RESTful
  - Message-oriented - WS*
  - Event-oriented - WS*
  
Only resource orientated architectural styles uses a RESTful approach. The other three use standardised Web Service Specifications.
  
10. Which of the following is NOT true of an architectural view of a software system?

  - Views the system as a set of components and connectors
  - Allocates of functionality to components
  - It is a detailed description of the design of the system
  - Is a high level view of the system with enough detail to assess the likely risks of the design

**Answer** - The architectural view for a software system is not designed to be a detailed design. The purpose of it is to be a high level view of the entire system, where requirements are set to components and the communication methods defined. It is used to show how components in a system will communicate with each other, and which component will do what.

It is not designed to describe exactly how each component will perform its task.
