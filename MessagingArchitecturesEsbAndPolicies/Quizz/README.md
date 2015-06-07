## Messaging, ESB and Policies

1. Identify each of the following policy assertions as to whether or not they are "on the wire".
	
  - QoS
  - Transport protocol selection
	- Authentication
	- Privacy
	
**Answer** - QoS and Privacy are policy assertions that are not "on-the-wire" and the other two are. "On the wire" are policy assertions that are done dynamically for a service when it is invoked. 

Both QoS and Privacy are non computational policies that need to be defined for a service.

2. In JMS an "client" refers to: (note - more the one answer may be true)

	- A JMS message broker that handles the message
  - An application or process the receives and consumes a message
  - There is no such thing as a "client" in JMS. Just message consumers and producers.
  - An application or process the creates and sends a message
  
**Answer** - A JMS client is an application or process that can either publish/produce or subscribe/consume to other applications or pocesses. 

3. Match the term to the description
	
  - Policy assertion
  - Policy expression
	- Policy attachment
  - Policy subject
	- Policy operation
	- Policy 

A. An informal abstraction that is used to refer to the set of information that is being expressed as policy assertions
B. Represents an individual preference, requirement, capability, or other property
C. An XML Infoset representation of one or more policy assertions
D. Enables to construct different logical combinations of policy assertions
E. An entity, e.g., an endpoint, object, or resource, to which a policy expression can be bound.
F. The mechanism for associating policy expressions with one or more subjects

**Answer**

  - Policy assertion - **B**
  - Policy expression - **C**
	- Policy attachment - **F**
  - Policy subject - **E** 
	- Policy operation - **D**
	- Policy  - **A**
	
4. In JMS point-to-point communication each message queue is associated with 

  - There are no restrictions on who can access the message queue.
  - Any number of message consumer
  - Only one message consumer
  - Exactly one message producer
  
**Answer** - Point-to-Point communication in JMS functions as a "Store and Forward" mechanism. It means that any number of publishers/producers can send messages to the queue, but only one subscriber/consumer can retrieve the message.

5. In JMS publish-subscribe communication each topic is associated with 

  - There are no restrictions on who can access the message topic.
  - Only one message consumer (subscriber)
  - Exactly one message producer
  - Any number of message producers (publishers)
  
**Answer** - A topic in the JMS publish-subscribe model refers to the container/queue that publishers push the messages to. It is up to the consumer to maintain a connection to the topic to retrieve the message. Any number of subscribers/consumers can register themselves to the topic to get the retrieve the message, it is up to the consumers/subscribers to notify the topic that the message has been received. 

Only a single publisher can publish to the topic.

6. Select the best answer. The WS-ReliableMessaging protocol can support the following aspects:

  - Both the sender and recipient of a message must know whether or not a message was actually sent and received.
  - Makes sure that the message was sent once and only once to the intended recipient.
  - Guarantee that the received messages are in the same order as they were sent.
	- All of the above
	
**Answer** - Reliable messaging protocol can support how a message can be received, at most once, at least once, exactly once and in order. All of the above actions are aspects of the WS-ReliableMessaging protocol.

7. Select which of the following answers are correct (there may be more than one). Enterprise Services Buses:

  - Incorporate MOM functionality
  - Can combine features from different types of middleware into one package
  - Provide message routing
  - Can connect non WS* applications
  - Can support business process management
  
**Answer** - ESB supports all of the above.

8. Which XML element encapsulates a Policy Alternative?
	
	- <wsp:All>
	- <wsp:ExactlyOne>
	- <wsp:Policy>
	- <wsp:PolicyAlternative>
	
**Answer** - All.

9. Which of the following answers is NOT correct? Middleware provides a functional set of interfaces to allow an application to:

  - locate other applications transparently across the network
  - access common domain-specific application features
  - provide services such as reliability, availability, authentication and security
	- shield software developers from low-level, tedious and error-prone platform details
	
**Answer** - access common domain-specific application features

10. Which of the following is NOT true of an architectural view of a software system?

  - It is a detailed description of the design of the system
  - Is a high level view of the system with enough detail to assess the likely risks of the design
  - Views the system as a set of components and connectors
  - Allocates of functionality to components

**Answer** - The architectural view (SOA) of a software system is not supposed to provide a detailed description of a system. It is supposed to provide just enough information about the system to clarify the requirements.

11. Which of the following is not generally considered a quality attribute of a service?

  - Security
	- Operations
	- Trust
	- Reliability
	- Performance
	
**Answer** - Operations.



