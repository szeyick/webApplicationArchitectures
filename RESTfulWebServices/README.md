# RESTful Web Services

- WS* prodominantly SOAP messages and WSDL interface descriptions to describe the end points.
- * (Standards) to allow enterprise services to interact with each other (QoS, Security, Descriptions)
- HTTP is used as the **transport** protocol for carrying SOAP messages
- BPEL (Business Process Execution Language) used to orchestrate how to communicate with web services.
- RESTful (Representational State Transfer) uses HTTP methods, and is resource centric
- REST uses HTTP as the **application** protocol, to share application state across clients and services.
- Non-REST approach using HTTP, encoding the URL in the header to pass the parameters through to the service.

- REST - exposes resources to client through a URI. Resources can be anything, not just application code.
- REST - is a client server architecture, there is no middleware involved.
- REST - is a design guide, not a standard.
- REST - the URI contains the link to the resource, and the parameters that the service needs.
- REST - using HTTP (CRUD), provides a uniform interface for accessing a service.
- REST - URI - defines the target address, verb defines the (CRUD) operation, Accept/Content Type is the format that the information will be presented in, and other headers.
- REST - uses standard HTTP error codes (200 OK, 404 Not Found etc)
- REST - complex queries may require a form to add multiple values to the URI for the service to process.
- REST - HTTP provides a generic interface, the structure of the message is independent from the content.
- REST - **Safe Methods** - Invocations that will not change the state of a resource (GET)
- REST - **Idempotent Methods** - Repeated Invocations will not change the result of the invocations (GET, PUT, DELETE), POST will update a resource.
- REST - resources are information resources, not domain objects. Because of the limited CRUD commands, we may need to separate resources (order resource, payment resource) to perform commands. For example, a DELETE on a combined order, payment resource will not know which to delete.
- REST - can use local cache and reverse proxy to improve performance and stability.
- REST - language independent, does not require middleware.
- REST - advantages : simple generic interface, CRUD operations, loose data coupling, no middleware, stateless, fast caching, scalable, resources links can be changed, client driven.
- REST - disadvantages : Not industry standard (No WSDL), lack of tool support, does not integrate easily, exposing URI's can lead to security flaws, legacy systems built on RPC, PUT is not widely used as it can be blocked on some browsers, stateless.

### WS* SOAP Architectures

In the beginning enterprise services were coupled together using CORBA, MoM, ESB approaches. These middleware technologies acted as a broker between distributed software systems.

As time evolved the landscape of distributed systems changed. Many large vendors developed their own middleware products to manage complex systems such as IBM Web Sphere, WSO2.

**RPC**, **Message Orientated** and **Event Orientated** architectural styles use the standard WS* protocols.

WS* views HTTP as a **transport protocol** to carrying SOAP (Simple Object Access Protocol) messages

### REST (Representational State Transfer)

REST uses **HTTP as the vehicle for transferring data and performing operations between web services over the Internet (CRUD)**. It is not a standardised architecture and acts as more of a guideline for development. It uses HTTP methods to **share application state** across the network.
However HTTP is such a generic message service, that **not all HTTP based approaches are classified as RESTful**. 
For example, you could put method calls in the HTTP message headings to call specific functions in another web service. It functions like a RPC call rather than simply passing the data around to be manipulated.

http://api.flick3.com/services/rest?api_key=xxx&**method=flickr.photo.search**&tags=penguin

The URL contains **method=flickr.photo.search**, which places method names and arguments in a **GET** message.

**Resource Orientated** architectural styles use RESTful protocols.

### Architecture

All data in REST is referenced with a URI. All resources are comprised of unique identifiers.

It follows a client-server architecture, and the application state is driven by the client updating the resources. It updates resources across the network by using links provided by the server.

Most designs for systems using the REST approach can fit into the CRUD model, where you map those operations to the functional operations of the system.

**resources** can be anything, a SQL query, text file, a program, something that you wish to perform an operation on. Each resource can be represented in different ways to the user/service. This is often required as different clients or services can reference the same resource and may require them to be interpreted differently.

![alt text][resources]

[resources]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTfulResources.png "RESTful References"

### Unique Identification

As mentioned, all resources in REST are referenced with a unique URI.

![alt text][logo]

[logo]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTUri.png "Unique URI References"

### REST Requests

REST uses a resource orientated design meaning that for each particular action (i.e createOrder, processOrder) in a application, it refers to those actions through specific CRUD interface calls.

To compose a query, we need to build a URI string, which connects the client to the particular reference object.

- **URI** - Identifies the target.
- **Verb** - One of the CRUD commands to perform an operation on the resource (PUT, GET, POST, DELETE).
- **Accept/Content Type** - How to represent the information (the format).
- **Other Headers** - Additional elements to assist in the processing context.

Complex queries may be harder to perform using the CRUD system. An idea would be to provide a form for the client to fill in to provide additional information in the URI.

REST Interfaces follow a standard pattern for all sorts of requests, rather than user driven interface definitions.

![alt text][interface]

[interface]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTInterface.png "REST provides uniform interfaces"

### REST Example

In this example, we'll show how CRUD operations are used along with URI's to access different areas of a web service.

- The flow here represents a REST request to the web server to GET all parts. The URI accesses a specific area of the web server that will manage this request, it will send a response back to the client.

![alt text][RESTRequest]

[RESTRequest]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTRequest.png "REST request to retrieve"

- In addition, we can request for a specific part by using the same GET request but with a different URI. This allows the web server to process the request with the part number to return the correct information to the client.

![alt text][RESTSpecificRequest]

[RESTSpecificRequest]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTSpecificRequest.png "REST request to retrieve specific part"

- Finally, again by changing the URI and performing a PUT request, we can perform a different action. This time it would be to ask the web server to process our part order.

![alt text][RESTProcessRequest]

[RESTProcessRequest]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTRequestOrder.png "REST request to process order"

### Error Handling

Because REST does not have a standard, errors during execution of requests on a web service will return standard HTTP error codes (i.e - 400, 404, 204, 200).

### HTTP Semantics

- Safe methods **will not change the state of the resource** (GET)
- Idempotent methods **will not change the result so long as the method argument contains the same parameters** (PUT, GET, DELETE).

| Verb (CRUD)   | Safe          | Idempotent  |
| ------------- |:-------------:| -----------:|
| GET           | YES           | YES         |
| PUT           | NO            | YES         |
| POST          | NO            | NO          | 
| DELETE        | NO            | YES         | 

### Caching

- REST can take advantage of web caching techniques (client and server caching) to improve performance and scalability by caching pages and resources that are called frequently. This does have the disadvantage of synchronisation issues when the data on the server is updated.

### Principles of RESTful design

- URLS to resources should contain **nouns** rather than verbs.
- How to represent the information in the resource.
- Consider how the client interacts with the data (read-only, modify) as the resources can be made accessible using specific CRUD requests.

### Building REST Web Services

- Any language can be used so long as the URI can reach the particular resource.
- Can use servlets to create the REST interface.

### Advantages

- Simple CRUD operations and standard HTTP error codes.
- Loose coupling by referencing resources through URIs (However we still need to know the exact URI)
- Data can be represented in many ways.
- Services are stateless, providing highly scalable services that are quick (caching)
- URIs can be late binded and do not need to be known beforehand by the client, links to resources can be changed dynamically. (**Loose interface and address coupling**
- Good for client driven services

### Disadvantages

- No defined standard.
- Integration is difficult with middleware as it requires knowledge of how the middleware works.
- Exposes the resource directly by referencing it through a URI.
- Difficulty integrating with legacy systems as they're based on RPC messaging.
- Not all browsers support PUT command.
- Clients and services need to exchange application state with each request/response. (Polling)
