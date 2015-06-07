## SOAP (Simple Object Access Protocol) Quizz

1. In the following SOAP body with RPC binding and "literal" binding on the operation, where is the POtype element defined? 

```
<?xml version= "1.0" encoding= "UTF-8" ?>

<soap:Envelopexmlns:soapbind="http://schemas.xmlsoap.org/soap/envelope"
       xmlns:tns="http://supply.com/PurchaseService/wsdl ">
     <soap:Body>
           <tns:SendPurchase>
               <POtype>
                   <PONumber> 223451 </PONumber>
                   <PODate> 10/28/2004 </PODate>
                </POtype>
                ……
           <tns:SendPurchase></soap:Body>
</soap:Envelope>
```
	
	- In an arbitrary namespace
  - In the SOAP header
  - In the associated WSDL document
  - In the SOAP body
  
**Answer** - The POtype element will be defined in the associated WSDL document. It should match with the **\<types\>**, either simple or complex that are defined in the document.

2. A SOAP message may carry application-specific data, a fault, or both.
  
  - True
  - False

**Answer** - A SOAP message can only carry application-specific data or a fault. It cannot contain both.

3. How many "Body Entry" elements can a SOAP "Body" element  contain?

  - Exactly one 
  - Zero or one
  - Zero or many
  - At least one
  
**Answer** - Within a SOAP message, the **\<Body\>** element is mandatory. However if it is used, it can contain at 1 or more body entry elements. This means that it can contain **at least one** element.

4. How many Header elements can a SOAP Envelope contain?

  - At least one
  - Zero or many
  - Zero or one
  - Exactly one 

**Answer** - A header element is optional within a SOAP message. Within the header message there can be many header entries, however a header element is a **zero or one** relationship with the SOAP envelope.

5. SOAP intermediaries are referenced in:
	
  - The SOAP Envelope
	- A SOAP Header
	- The body of SOAP message
	- Any of the above
	- The is no such thing as a SOAP intermediary. All processing of the SOAP message is done at the Receive node.
	
**Answer** - SOAP intermediaries are a middle node that gets the message before it is forwarded to the intended receiver. It is referenced within the SOAP envelope in the header element.

6. SOAP supports
  
  - Only RPC communication style
	- Only Document (message) communication style
	- Both RPC and Document communication styles
  - SOAP does not support communication styles. It is only a message format.
  
**Answer** - SOAP supports both RPC and Document style communication. In RPC, the method name being called is required in the message along with the method arguments, whereas in document style, only the XML fragment is required, it is up to the middleware to decode the message and route it to the correct method.

7. SOAP only uses HTTP as a transport protocol
  
  - True
  - False

**Answer** - SOAP can use HTTP as a transport protocol, but it can also use HTTP, SMTP, JMS or other types of transport.

8. What type of style is the following request message:

```
env:Envelope
 xmlns:SOAP=“http://www.w3.org/2003/05/soap-envelope”
 xmlns:m="http://www.plastics_supply.com/product-prices">
    ...
 <env:Body>
      <m:GetProductPrice>                   
          <m:product-id>  450R6OP  </m:product-id >
     </m:GetProductPrice >
 </env:Body>
</env:Envelope>
```

  - RPC style
	- Document style
	- Could be either
	- Neither
	
**Answer** - The SOAP message contains a GetProductPrice, meaning that it is of the RPC style as the element should reference the GetProductPrice method. 

For it to be a document style message, it should only contain the product-id or any other parameter.


