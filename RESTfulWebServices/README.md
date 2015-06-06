# RESTful Web Services

### WS* SOAP Architectures

The early form of distributed enterprise services were coupled together using CORBA, MoM and ESB approaches. These middleware technologies acted as a mediator between different distributed software systems. BPEL (Business Process Execution Language) describes how to communicate between services (assigning of data, invoking services).

As time evolved the landscape of distributed systems changed. Many large vendors developed their own middleware products to manage complex systems such as IBM Web Sphere, WSO2.

**RPC**, **Message Orientated** and **Event Orientated** architectural styles use the standard WS* protocols.

In WS*, **HTTP** is viewed as a **transport protocol** which carries SOAP (Simple Object Access Protocol) messages between clients and services. A WSDL (Web Service Description Language) interface is also used in WS* that describes a how clients will connect to the service implementation (end service).

The * (Standards) in WS* refers to the standards that are used to allow for enterprise services to talk to each other (QoS, Services, Descriptions).

### REST (Representational State Transfer)

REST uses **HTTP** as an application protocol, to transfer data and operation information between web services over the internet. This differs from the WS* method which uses HTTP as a **transport protocol**. It is not a standardised architecture and acts as more of a guideline for development. It uses HTTP methods (CRUD) to **share application state** across the network.

However HTTP is such a generic message service, that **not all HTTP based approaches are classified as RESTful**. 
For example, you could put method calls in the HTTP message headings to call specific functions in another web service. It passes the method to call as a parameter in the URL.

http://api.flick3.com/services/rest?api_key=xxx&**method=flickr.photo.search**&tags=penguin

The URL contains **method=flickr.photo.search**, which places method names and arguments in a **GET** message.

**Resource Orientated** architectural styles use RESTful protocols.

### Architecture

All data in REST is referenced with a URI and all resources are comprised of unique indentifiers. This allows external clients to connect to a particular resource in a web service. The URI contains the location of the service, and also the data the service requires.

It follows a client-server architecture meaning that there is no middleware required to mediate the communications. The client uses the URI endpoint to communicate directly with the server. Because of this model, the application state is driven by the client. 

Designs for systems using the REST approach will need to fit into the CRUD model. This means that the operations that the service performs has to call within the GET, PUT, POST, DELETE commands.

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

- Safe methods **multiple invocations will not change the state of the resource** (GET)
- Idempotent methods **multiple invocations will not change the result so long as the method argument contains the same parameters** (PUT, GET, DELETE).

| Verb (CRUD)   | Safe          | Idempotent  |
| ------------- |:-------------:| -----------:|
| GET           | YES           | YES         |
| PUT           | NO            | YES         |
| POST          | NO            | NO          | 
| DELETE        | NO            | YES         | 

Multiple POST requests will result in additioanal resources being created as the purpose of POST is to create new resources.

In REST, resources are seen as information sources and not domain objects. Because we have only 4 CRUD commands to use, sometimes in the design we may need to separate resources (single end point refers to a single operation) otherwise we may try to perform the same CRUD command. For example, a order fulfillment resource may contain both a order and payment resource. If we use a DELETE CRUD, we don't know whether to delete the order itself or delete the payment.

In instances like that, we may need to split them into individual resources (one payment and one order).

### Caching

- REST can take advantage of web caching techniques (client and server caching) to improve performance and scalability by caching pages and resources that are called frequently. This does have the disadvantage of synchronisation issues when the data on the server is updated.

### Principles of RESTful design

- URLS to resources should contain **nouns** rather than verbs.
- How to represent the information in the resource.
- Consider how the client interacts with the data (read-only, modify) as the resources can be made accessible using specific CRUD requests.

### Building REST Web Services

- REST web services do not rely on middlware and thus the implementation can be written in any language.
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

- No defined standard (No WSDL).
- Integration is difficult with middleware as it requires knowledge of how the middleware works.
- Exposes the resource directly by referencing it through a URI.
- Difficulty integrating with legacy systems as they're based on RPC messaging.
- Not all browsers support PUT command.
- Clients and services need to exchange application state with each request/response. (Polling)
