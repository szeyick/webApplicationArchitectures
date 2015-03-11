# Introduction to Web Application Architectures

### Key Definitions
1. Functional and Non-Functional Properties - 
    - Functional Properties describe what the service is to do and how it does it.
    - Non-Functional Properties describe metrics, costs, KPI's, capacities of the system.

2. Stateless vs Stateful Services -
    - Stateless Services are services that can be invoked repeatedly without maintaining state or context.
    - Stateful Services preserve context and can change from one invocation to another.

3. Granuality -
    - Fine grained services, operate through a request/response mechanism.
    - Course grained services are more complex services that often interact with other services and aggregate a response.

4. Synchronicity - 
    - Synchronous communication between systems is where the system who sends the request waits for a response before continuing onto other tasks.
    - Asynchronous communication between systems is where the system who sends the request can continue performing other tasks whilst awaiting a response.

5. Service Interface and Implementation -
    - The interface defines the functionality accessible by the outside world.
    - The implementation is the concrete implementation of the interface definitions. 

### Web Services, what are they?

In the most basic sense, a web service defines the method of communication between two devices over a network. Such examples of this would be a client browser and a remote server.

It provides a function, hence the name **service** and works similar to a request/response mechanism.

### Real World Examples

#### Online Purchasing
When we purchase items online (eBay, Amazon etc), we usually perform these tasks through a web browser. When we finalise the purchase and pay, we send a request off with the purchase information to a remote server that processes the sale.

Information in the request that we send can contain -

1. Buyer address.
2. Item name and quantity.
3. Credit card information.

When this request arrives at a central server, it may be dispatched off to several other servers to process individual requests for processing the buyer address, processing items and payment information. The central server gets the responses from all the servers and then sends the invoice back to the user. 

This flow represents how a web service works (The Purchase Order Server acts as a mediator to other web services):

![alt text][logo]

[logo]: https://github.com/szeyick/webApplicationArchitectures/blob/master/IntroductionToWebArchitectures/resources/WebService.png "Purchasing Web Service"

### Enterprise Computing

In enterprise computing there are many more factors that need to be considered when developing a web application -

1. Data needs to be persisted -> Requires concurrent access to allow many users to access simulatneously.
2. Processing can be costly (time) -> Requires asynchronous access that does not stop the user from performing other tasks.
3. Configurable -> Requires system to be loosely coupled so components can be changed.
4. Diverse systems -> large companies can have many different services coupled together to form a system.

Enterprise orientated computing is sometimes refered to as Web Services. The idea here is to create loosely coupled systems that communicate with each other through the <b>exchange of documents</b>.

### Web Service Function

Web services perform business functions such as -

1. A singular task such as withdrawing funds or checking the weather for a particular day.
2. Providing an application such as a bank application or health insurance application.
3. Automation of business processes such as purchasing office supplies.

These individual services can be mixed and matched together to provide a complete system. 

Each system costs money, but because of their loosely coupled nature, an organisation does not always neccessarily need to build the system in-house and can offset the costs by <b>paying to use</b> or <b>leasing</b> it from a third party.

### Types of Web Services

#### Information Services
These services are very simple, they only provide access to content through **request/response** communications. An example of this would be access to weather and stock information or news aggregators.

#### Complex Services
Complex services involved the assembling of information from other services. An example of this would be our online shopping example above, sourcing (Alibaba) or online banking systems.

### Advantages of Web Services

#### Within a business
1. Speed up and reduce cost of integration - Communication between web services is standardised.
2. Save on infrastructure deployment and management costs - Using 3rd party services to manage tasks not core to business operations.
3. Reduce required staff - Less software services to maintain means less staff required within the business.
4. Improved reuse and flexibility - Mix and match coupling services allow businesses to adapt to changes.

#### Between Businesses
1. Provide services to business customers - Linking services between business partners (Insurance brokers)
2. Accessing partner and suppliers - Directly accessing supplier stock.

These are achieved through **standards (JSON, XML communication)**, **simple integration** and **dynamic changes**.

#### REST

REST based web services (Representational State Transfer), is a data centric approach to developing web services. Data with internal state is emphasised here, where services perform operations on the data.

It is a lightweight approach as it is based on HTTP where you do not require any additional middleware.

REST generally follows the core CRUD (Create, Retrieve,  Update, Delete) HTTP operations.

- GET - receive information on a resource
- POST - create a new resource 
- PUT - modify an existing resource
- Delete - delete a resource 
- HEAD and OPTIONS are also used to get metadata and supported HTTP calls.

In REST everything is referenced as a URI. 

Resource Orientated architectures are examples of RESTful architectures.

##### Web Service Standards

WS provide an additional set of standards on top of HTTP for the development of web services. It is considered heavier than REST based services as there is an additional layer of middleware or frameworks are used to build services.

RPC, Message Orientated and Event Orientated architectures are example of Web Service Architectures.
