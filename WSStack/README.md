# WS Stack, XML and WSDL

From previous topics, we know that WS* approaches refer to RPC, Message Orientated and Event Orientated architectural styles. It can sit on top of existing application protocols to send messages through a network (HTTP, HTTPS, SMTP).

## Message Exchange Patterns (RPC - Remote Procedure Calls)

RPC's are synchronous operations that follow the request/response pattern. The code is generally the same between the client and server, so the client essentially calls the same function on the server. This results in **tightly coupled code** since changes in either can stop the RPC from functioning correctly and RPC requires knowledge of the invoking method names.

RPC requests usually comprise of using **method name + arguments**, the response will contain the service response or an acknowledge.

## Message Orientated API's

Can be both synchronous and asynchronous messsage types. The client and server communicate through messages, meaning that if we change the message, it will not break the interface. Either the client and server can choose to ignore the newer or unused parts of the message without affecting the behaviour.

The messages that are exchanged between client and server are constructed through an XML schema.

### Request/Response Messaging

![alt text][requestResponse]

[requestResponse]: https://github.com/szeyick/webApplicationArchitectures/blob/master/WSStack/resources/messageRequestResponse.png "Request/Response Example"

As the name stipulates, it is a messaging operation where a message is received and a response is returned. The addition of the **output** element means that the web service is expected to respond.

```
<wsdl:operation name="DispatchOrder">
  <wsdl:input message="tns:DispatchOrder_Message"/>
  <wsdl:output message="tns:TrackingNumber_Message"/>
</wsdl:operation>
```

### One Way Messaging

Is a messaging operation where the message is sent by the client, but a response is not expected. An example of a one way message in a programming language would be a trigger of a `void doSomething()` method call.

A one way message is defined in the schema as a **input** element without a corresponding **output**. This illustrates that no response is expected to be sent.

```
<wsdl:operation name="SubmitOrder">
  <wsdl:input name="order" message="tns:SubmitOrder_Message"/>
</wsdl:operation>
```
 
### Notification Messaging

Is a messaging operation where the message is sent by the service/server to registered clients, but does not expect a response. It is similar to the one way message, but from the server side. 

As such, the message schema will contain a **output** element and no **input** element.

```
<wsdl:operation name="SendInvoice">
  <wsdl:output name="invoice" message="tns:SubmitInvoice_Message"/>
</wsdl:operation>
```

### Solicit Response 

A message operation that would be the opposite of request/response. In this instance, the service/server sends the request to the client expecting a result. As this is the opposite, the message schema for the order of **input** and **output** elements are the opposite of the request/response schema.

```
<wsdl:operation name="VerifyDelivery">
  <wsdl:output message="tns:VerifyDelivery_Message"/>
  <wsdl:input message="tns:DeliveryReceived_Message"/>
</wsdl:operation>
```

## Message Orientated Middleware (MoM)

Middleware functions as a sort of broker/mediator of messages, where it manages and directs where the messages go.

MoM provides the following functions
- Queuing
- Event driven processing (publish/subscribe pattern)
- Messages are serialised, delivered once.
- Message structures are sent in XML, so the middleware is unconcerned with the message type.

## XML Schema

Is used for the validation of XML **instance** documents. The schema itself specifies the **structure** (elements, attributes) and the **datatype** of each element/attribute, essentially how the data should look like.

The schema is written in XML, so uses the same syntax as XML and is used to define WS standards. A validator is used to ensure that the data can be accepted/used by the recipient.

XML in a web service can be used for the following -

- Storing the service contract in a registry.
- Configuring the service
- Structure of the data from the message so the server can parse the XML.

## Namespaces

Is a collection of names, contained within a URI reference (generally a file somewhere) that stores the valid element types and names that can be used by a schema to define an XML document.

Every XML schema uses **at least two** namespaces to provide the vocabulary for the document. The main one being the namespace provided by W3C that contains all the generic types that can be used, and sometimes a user defined vocabulary.

The second, non-default namespace will need to be referenced by a qualifier (i.e. xmlns:xsd="http:...."). This means that elements, attributes or any words within the document will need to be referred to by its qualifier <xsd:name>. 

The below defines a user created XML for defining a bookstore with the two namespace documents.
```
<?xml version="1.0"?>
<BookStore xmlns="http://www.bookstore.org"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           <!-- The schema location, tells the validator that the bookstore.org namespace is defined by the BookStore.xsd-->
           xsi:schemaLocation="http://www.bookstore.org
                                        BookStore.xsd">
           
           <Book>
           ....
          </Book>
</BookStore>
```
The corresponding XML schema for the bookstore could be defined as follows

```
<?xml version="1.0">
<!-- All XML schemas start with the <schema> tag -->
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
            targetNamespace="http://www.bookstore.org"
            xmlns="http://www.books.org" <!-- The default namespace -->
            elementFormDefault="qualified">
    <xsd:element name="BookStore"> 
    <!-- xsd points to the http://www.w3.org/2001/XMLSchema definition, meaning it must be used before every schema element-->
    </xsd:element>
</xsd:schema>
```

Because we defined the bookstore to contain the default namespace, it means that the W3C XMLSchema needs to be referenced through the "xsd" qualifier, otherwise it will have no idea where to look for the standard element or attribute names. We can always change this around so that the W3C schema is taken as default and the bookstore to be the additional namespace, which becomes - 

```
<?xml version="1.0">
<!-- All XML schemas start with the <schema> tag -->
<xsd:schema xmlns="http://www.w3.org/2001/XMLSchema" 
            targetNamespace="http://www.bookstore.org"
            xmlns:bs="http://www.books.org" <!-- The default namespace -->
            elementFormDefault="qualified">
    <element name="BookStore"> 
    ...
    </:element>
</xsd:schema>
```

Within a schema, elements can be classed as **global** if they sit as a **direct child of the schema element**. This allows them to be referenced anywhere within the schema itself.

Schema files can be imported into existing schema documents using the **import** and **include** element tags. Import allows access to elements and types in a **different namesapce** (different file), whereas include allows access to elements and tags in the **same namespace**, which is used if we have a large file with multiple schemas (`<xsd:schema></xsd:schema>`) defined.

### XMLSchema-instance Namespace
An additional namespace, http://www.w3.org/2001/XMLSchema-instance allows a namespace to be extended. Names within those namespaces are generally referenced through the **xsi prefix**. For example the xsi:noNamespaceSchemaLocation and xsi:schemaLocation allows us to tie a document to its W3C XML Schema.

www.corefilling.com provides a XML validation to ensure that the XSD and XML conform.

## Element Declarations

A **Element** in XML can be seen as an object, and is defined using the `**<xsd:element></xsd:element>**` tag. Anything inbetween the opening and closing tags of the element is seen as part of the element.

Elements can be comprised of -

1. A name - `<xsd:element name="nameOfElement"></xsd:element>`
2. A type - `<xsd:element type="xsd:string></xsd:element>` (The default type is a string if no type is defined)
3. Cardinality - `<xsd:element minOccurs="3" maxOccurs="3"></xsd:element>` (Number of elements)

### Simple Types -

Simple types generally refer to primitives such as strings and integers. There are three types of simple data type structures.

1. Build-in Types - Primitives
2. Derived Types - Build from primitives or other derived stypes.
3. User Derived Types - Created types comprised of the first two.

With User Derived Types we can build our own derived types by using a primitive and attaching our own properties (restrictions) onto it.

```
<xsd:simpleType name="name">
  <!-- The restruction uses a primitive type as the "base" to build on top-->
  <xsd:restriction base="xsd:source>"
    <!-- A facet is the restrictions that we would like to place ontop of our type.  -->
    <xsd:facet value="value"/>
    <xsd:facet value="value"/>
    ...
  </xsd:restriction>
</xsd:simpleType>
```

### Complex Types

A complex type is a type that can include both elements and attributes. It is defined using the `<xsd:complexType>` and is used like a composite object. It has additional defintions to define how the type is structured.

1. `<xsd:sequence>` - The ordered sequence of data between the start and end of the tag.
2. `<xsd:choice` - The choice of the contained data between the start and end of the tag.
3. `<xsd:all>` - All the contained data between the start and end tag in any order.

Again they can also be derived much the same as simple types, in similar style as well.

## Attribute Declarations

A **Attribute** on XML defines the properties of the Element structure and is defined using the `<xsd:attribute></xsd:attribute>` tags, after the declaration of the Element.

Attributes can be comprised of -

1. A type - `<xsd:attribute type="attributeType"></xsd:attribute>`
2. Uses - defined whether the attribute is needed, Optional (Not required), Required and Prohibited (Cannot be used on a given element)
3. Fixed and Default Values - `<xsd:attribute fixed="2000"`/> and `<xsd:attribute default="2001""/>`

## WSDL - Web Service Description Language

Describes the interface between the developer and the user. It is the users job to find the description and interact with the web service through the defined interface.

It is an XML based description language, where the user interacts with the web service through the interface and not the concrete implementation. This allows the service to hide its implementation and also allows for the service to be language independant since the user doesn't need to know.

The language is designed to be created and read by machines and can be generated from objects or IDE tools.

### Web Services in Context

The following is described by WSDL 

- What the service can do - Its **functionality** (WDSL)
- How well the service can do it - Its **qualities** (Other WS standards)
- How to use the service - Its **usage** (WDSL)

### WSDL Structure

The intention of WDSL is to provide a means of communication between the client and server without them directly knowing about each other. It defines how to reach the implementation of the services that are available to a particular web service.

The document itself describes -
1. **What** the service does and the operations that it provides.
2. **Where** the service resides, the address (URL)
3. **How** the invoke the service, the formats to access the interface.

The structure of the WSDL is separated into distinct sections -
1. ** Service Interface Definition** - Defines all the **operations** that the service will provide, **parameters** and the **abstract data types**.
2. **Service Implementation** - **Binds** the interface to the **concrete network address**, **protocols** and the **data structures**. Essentially the link between the interface and the concrete implementation.

### WSDL Document Definitions

#### Interface Definitions
- **<types>** The data type definitions
- **<message>** The operation parameters
- **<operation>** The description of the actions
- **<portType>** The definition of the operations (The interface)
 
#### Concrete Definitions
- **<binding>** Bindings to operations
- **<port>** Bind to a end point
- **<service>** Location/Address for each binding.

Additionally, **<import>** is used to reference other XML documents.

### WSDL Structure

An example of the WDSL interface structure is below -

```
<?xml version="1.0"?>
<wdsl:definitions <!-- xsd namespaces are defined here --> /">
  <wdsl:types>
    <!-- xsd type definition for message parts here -->
  </wdsl:types>
  <!-- list of messages -->
  <wsdl:message name="abcRequest"> <!-- List of message parts here --> </wdsl:message>
  <wsdl:message name="abcRespond"> <!-- List of message parts here --> </wdsl:message>
  
  <!-- list of port types -->
  <wdsl:portType name="xyz">
    <!-- list of operations-->
    <wdsl:operation name="abc">
      <!-- The input/output messages are linked to the list of messages that the service can receive/respond to list above -->
      <wdsl:input message="tns:abcRequest"/>
      <wsdl:output message="tns:abcResponse"/>
  </wdsl:portType>
</wdsl:definitions>
```

- **Namespaces** - The namespace declarations are done in between the `<wdsl:definitions>` tags.
- **Types** - The types for the WSDL are declared between the `<wdsl:types>` tags, and are constructed as per types defined above.
- **Messages** - The message definition (structure) is defined between `<wsdl:message>` tags. If we compare RPC and Document Style `<wsdl:message>`, its similar, but RPC refers to the **type** whereas document links to the **element**.
- **Port Type** - Is a logical grouping of `<wdsl:operation>` (operations). It describes the operations that the web service supports, the message mode (input/output) and the type (message structure).
 
An example of the WDSL concrete implementation is below -

```
<?ml version="1.0"?>
<wsdl:definitions <!-- xsd namespaces defined here --> />
  <!-- Abstract section goes here - It can be imported -->
  <wsdl:binding name="portBindingName" type="tns:nameOfPortFromInterfaceDocument">
  </wsdl:binding>
  
  <wsdl:service name="nameOfService">
    <!-- List of ports -->
    <wdsl:port name="nameOfPort" binding="portBindingName">
      <!-- This port is associated to a port defined in the binding above -->
      <!-- The binding links to a particular address or URI, where the service is located -->
      <soapbind:address location="http//myshop.com:8080/orderingService"/>
    </wdsl:port>
  </wdsl:service>
</wsdl:definitions>
```
- **Binding** - The `<binding>` element defines how the client and web service should exchange messages. Furthermore, the binding element may contain the **protocols** (SOAP, HTTP), **messaging styles** (RPC, Document) and **formatting styles**.
- **Port** - The `<port>` element defines the location of the web service. It is possible for multiple port elements to refer to the same URI address as it can be used for load balancing.
- **Service** - The `<service>` element contains a collection of ports, the name for the serive must be unique in the document.
