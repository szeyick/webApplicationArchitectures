L# SOAP - Simple Object Access Protocol

The protocol in which messages and sent between the client and server. This differs from RESTful services as it is its own protocol whereas in REST it uses HTTP as the protocol (GET, PUT, DELETE) SOAP provides an additional layer of abstraction for messages to be sent.

- WDSL abstraction defines the interface that exposes the methods or operations of the web service to the outside world. 
- the concrete definition contains the end points that is the point that invokes the service. It implements from the abstract interface, this mapping is done by the binding which acts as the mediator or delegate that defines which interface maps to which concrete implementation.
- the binding tag binds the interface and defines the style of the message (can be SOAP), the binding can state that which operation the SOAP message will be sent to.

## inter application communication (history)
- to make distributed computing easier, in lower level programming they had the concept of opening ports of machines.
- using middleware, it can be used to grab objects in other machines using object orientated middleware (CORBA, Java RMI)
- thre advantage here is that you can refer to objects on other machines through references just like in a local application, and it is OO based. A disadvantage is that it is tightly coupled as it is reliant on knowing the object reference ID which someone needs to hold the records of object IDs when they are created
- another disadvantage is that ports are required to be opened, making it hard to use in high secured fire walled organisations. As firewalls are generally configured to let HTTP through and not much else.

## SOAP

- An XML based messaging structure, that follows a defined format.
- Loose coupled and designed to work with WSDL, and the WSDL specifies the structure and takes the SOAPS format as specified by the WSDL.
- SOAP is primarily used for server to server communication.

### Message Format
- has 2 parts, the header and body, the header can be optional.
- the header can take multiple entries called blocks and defines how the message can be read (i.e namespace, validation)
- the body contains the actual message
- the entire message structure including head and body can be seen as an envelope.

### when the message is sent

- it can send the SOAP message to an **intermediary** to validate the header to ensure that the message can be read by the service.

## SOAP Body
- contains the actual message data or a error message to be sent if the service cannot process it. It has to be one or the other but not both.

## Communicatoin

- supports RPC and document styled message.
- RPc style means that the message will contain the methods to call in the message body, whereas the document model is just an XML document and it is up to the service to figure it out.
- a error or fault message can be placed in the SOAP message to be returned when an error is detected

## SOAP over HTTP
- SOAP uses HTTP as transport to go between client and server.
- uses POST and GET, in POST the request and response are SOAP structure message whereas in GET only the response is SOAP.
- the middleware in SOAP strips the HTTP and leaves the SOAP XML message for the service or client to process, it does not need to worry about how to decipher the HTTP message.

## Advantages

- Standard format
- Portable as it uses XML
- uses a http transport so is friendly to be passed between systems with firewalls

## Disadvantage
- very big message as it is structure is completely written in XML.
- does not persist state, it is stateless so maintain state, the data may need to be saved, or current state sent back and forth.

