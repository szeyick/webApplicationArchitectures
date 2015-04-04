# SOAP - Simple Object Access Protocol

SOAP sits in the **message** layer in the web services stack. It is the protocol that is responsible for sending messages between a client and the server. It differs from RESTful services as it is its own protocol whereas REST uses HTTP as the protocol (using GET, PUT, DELETE). SOAP on the other provides an additional layer of abstraction for messages to be sent.

## WSDL and SOAP

The WSDL (Web Services Description Language) defines the interface that exposes the operations (methods) of a particular web service to the outside world. It is comprised of **two parts**, the **abstract interface** and the **concrete definition**. The concrete definition contains the end points that link directly to the methods that invoke the service. The abstraction links to the concrete definition through the **binding** that states which interface operation maps to which concrete operation. 

The **<binding>** tag that maps the interface to the concrete defintion can also be used to define the style of the message. The style of the message can be defined as SOAP, meaning that the operation (method) shall receive a message in the structure of a 
SOAP message.

The image below illustrates the link between the interface and concrete parts of the WSDL.

![WSDL Interface and Concrete](https://github.com/szeyick/webApplicationArchitectures/blob/master/SOAP/resources/wsdlInterfaceToConcrete.png "Connection between interface and concrete")

## History of Inter-application Communication

The idea behind inter-application communication stems from the requirement of different systems needing to communicate with each other through a common means. Originally this was achieved with lower level programming where applications would be required to open ports on machines, which lead to a few security issues, especially in highly secured environments where there are firewalls.

Another idea was the use of **object orientated middleware** such as CORBA or Java RMI. This allowed application to access and retrieve objects on machines across a distributed system. The **advantage** by using OO middleware like this would be that it **allowed object access across a network just the same as if it were a local object**. A **disadvntage** of this is that it results in a tightly coupled system as individual components are **required to know the object reference ID that they wish to access**. This results in a manager to hold the records of object ID upon creation. 

A solution would be to use HTTP as most firewalls are configured to allow HTTP messages through. 

## SOAP

SOAP, Simple Object Access Protocol is an XML message based messaging structure that follows a standardised format. It is loosely coupled and designed to work with WSDL as it allows the message type to be defined in the definition. This allows for a SOAP formatted message to be processed by the web service. 

It is a protocol that is primiarly used for server to server communication. Since it uses the HTTP as the transport, it can be safely used even across firewalled applications. It is packed and unpacked by a SOAP based middleware thus reducing the amount of work to translate the message.

### Message Format

SOAP is based on **exchanging messages**, where the messages themselves can be best described as **envelopes** as the message contains the data that is to be sent. 

There is an **<Envelope>** element that contains two parts, the **<Header>** and **<Body>**. Only the **<Body** is mandatory. 

The **<Header>** contains entries called **blocks** that define how the message can be processed (i.e. namespace, validation).

The **<Body>** contains the actual message/data. The diagram below describes the structure of a SOAP envelope.

![SOAP Envelope](https://github.com/szeyick/webApplicationArchitectures/blob/master/SOAP/resources/SOAPEnvelope.png "The structure of a SOAP message")

### SOAP Envelope and Header Structure

```
<env:Envelope
xmlns:env=“http://www.w3.org/2003/05/soap-envelope” >
…
  <env:Header>
    <tx:transaction-id
      xmlns:tx=”http://www.transaction.com/transaction”
      env:mustUnderstand=”true”>
        512
    </tx:transaction-id>
    <notary:token xmlns:notary=”http://www.notarization-services.com/token”
    env:mustUnderstand=”true”>
      GRAAL-5YF3
    </notary:token>
  </env:Header>
……………
</env:Envelope>
```
### When the message is sent

When a message is sent, it can be first sent to an **intermediary** that can validate data in the header to ensure that the message can be read by the service before the body is unpacked. The message is routed to the intermediary to process that can return a fault if it cannot process the message in the header, without it ever reaching the service endpoint.

### SOAP Body

The body contains the actual message data (in XML) to be exchanged or processed. The **<Body>** element is mandatory and must be a direct child of the **<Envelope>**. The body element contains either the **application specific data** or a **error message** should a error be detected. It can only contain application specific data or an error message, never both. 

An example body element is shown below

```
<env:Envelope xmlns:env="http://www.w3.org/2002/06/soap-envelope">
... <!-- Header elements can go here -->
  <env:Body>
    <m:orderGoods
      env:encodingStyle="http://www.w3.org/2002/06/soap-encoding"
      xmlns:m="http://example.com/procurement">
      <m:productItem>
        <name>ACME Softener</name>
      </m:productItem>
      <m:quantity>
        35
      </m:quantity>
    </m:orderGoods>
  </env:Body>
```
### Communication Model

SOAP supports RPC and Document Styled messages. 

A RPC styled message is a SOAP message where the body element contains references to the methods to call in the web services.

```
<env:Body>
  <m:GetProductPrice>
    <m:product-id> 450R60P </m:product-id>
  </m:GetProductPrice>
</end:Body>
```
The RPC styled body above, will invoke the method with the name **GetProductPrice(String productID)**.

The Document (Message) style is a SOAP message where the body contains an XML fragment. It is up to the application (web service) to figure out whether the message is applicable to it or not.

```
<env:Body>
  <po:PurchaseOrder orderDate=”2004-12-02”
  xmlns:m="http://www.plastics_supply.com/POs">
    <po:from>
      <po:accountName> RightPlastics </po:accountName>
      <po:accountNumber> PSC-0343-02 </po:accountNumber>
    </po:from>
    <po:to>
      <po:supplierName> Plastic Supplies Inc. </po:supplierName>
      <po:supplierAddress> Yara Valley Melbourne </po:supplierAddress>
    </po:to>
    <po:product>
      <po:product-name> injection molder </po:product-name>
      <po:product-model> G-100T </po:product-model>
      <po:quantity> 2 </po:quantity>
    </po:product>
  </ po:PurchaseOrder >
</env:Body>
```

### Error Messages

SOAP provides a model for handling errors in the processing of messages.

```
<env:Body>
  <env:Fault>
    <env:Code>
      <env:Value>env:Sender</env:Value>
      <env:Subcode>
        <env:Value> m:InvalidPurchaseOrder </env:Value>
      </env:Subcode>
    </env:Code>
    <env:Reason>
      <env:Text xml:lang="en-UK"> Specified product did not exist </env:Text>
    </env:Reason>
    <env:Detail>
      <err:myFaultDetails
      xmlns:err="http://www.plastics_supply.com/faults">
        <err:message> Product number contains invalid characters </err:message>
        <err:errorcode> 129 </err:errorcode>
      </err:myFaultDetails>
    </env:Detail>
  </env:Fault>
</env:Body>
```

## SOAP over HTTP

SOAP uses HTTP as the transport mechanism to communicate between the client and server. It uses **POST** and **GET** requests.

In a **POST** message, the request and response are SOAP structured messages, whereas in a **GET** message, only the response is in SOAP.

SOAP uses the same error and status codes as HTTP, so it can be directly interpreted by a SOAP module. In addition, the SOAP middleware strips the HTTP away and leaves the SOAP XML message for the service to process. The service does not need to worry about how to decipher the HTTP message to extract the SOAP message. 

## Advantages

- Standard format.
- Portable as it uses XML.
- Uses a HTTP transport so is friendly to be passed between systems with firewalls.
- It is universally accepted and uses standards.

## Disadvantage

- Can result in large messages since the entire structure is written in XML.
- Does not persist state, SOAP is stateless, therefore to maintain state, the data may need to be saved or sent back and forth between services.
