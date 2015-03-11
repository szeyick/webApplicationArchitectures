# RESTful Web Services

### WS* SOAP Architectures

In the beginning enterprise services were coupled together using CORBA, MoM, ESB approaches. These middleware technologies acted as a broker between distributed software systems.

As time evolved the landscape of distributed systems changed. Many large vendors developed their own middleware products to manage complex systems such as IBM Web Sphere, WSO2.

### REST

REST uses HTTP as the vehicle for transferring data and performing operations between web services over the Internet (CRUD). It is not a standardised architecture and acts as more of a guideline for development.

However HTTP is such a generic message service, that not all HTTP based approaches are classified as RESTful. 

For example, you could put method calls in the HTTP message headings to call specific functions in another web service. It functions like a RPC call rather than simply passing the data around to be manipulated.

### Architecture

All data in REST is referenced with a URI. All resources are comprised of unique identifiers.

It follows a client-server architecture, and the application state is driven by the client updating the resources.

Most designs for systems using the REST approach can fit into the CRUD model, where you map those operations to the functional operations of the system.

**resources** can be anything, a SQL query, text file, a program, something that you wish to perform an operation on.

### Unique Identification

http://server:port/path/to resource?p1=v1&p2=v2 represents a URI.

### REST Requests

Accept/Content Type represents how you want to format the information.
POST is used for creating new instances or objects,
PUT is used for updating existing objects.

#### Error Handling

Because REST does not have a standard, errors during execution of requests on a web service will return standard HTTP error codes (i.e - 400, 404, 204, 200).

