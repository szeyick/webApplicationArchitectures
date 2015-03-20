# RESTful Web Services

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

**resources** can be anything, a SQL query, text file, a program, something that you wish to perform an operation on. Each resource can be represented in different ways to the user/service. This is often required as web services can talk to each other alongside talking to clients, which may require the same data in a different format.

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

1. The flow here represents a REST request to the web server to GET all parts. The URI accesses a specific area of the web server that will manage this request, it will send a response back to the client.

![alt text][RESTRequest]

[RESTRequest]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTRequest.png "REST request to retrieve"

2. In addition, we can request for a specific part by using the same GET request but with a different URI. This allows the web server to process the request with the part number to return the correct information to the client.

![alt text][RESTSpecificRequest]

[RESTSpecificRequest]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTSpecificRequest.png "REST request to retrieve specific part"

3. Finally, again by changing the URI and performing a PUT request, we can perform a different action. This time it would be to ask the web server to process our part order.

![alt text][RESTSpecificRequest]

[RESTSpecificRequest]: https://github.com/szeyick/webApplicationArchitectures/blob/master/RESTfulWebServices/resources/RESTRequestOrder.png "REST request to process order"

### Error Handling

Because REST does not have a standard, errors during execution of requests on a web service will return standard HTTP error codes (i.e - 400, 404, 204, 200).

### HTTP Semantics

- Safe methods **will not change the state of the resource** (GET)
- Idempotent methods **will not alter the result so long as the method argument contains the same parameters** (PUT, GET, DELETE).

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
