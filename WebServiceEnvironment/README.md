#Web Service Environment

This project contains notes about getting setup a development environment ready to begin building web applications. 

The different server installations do not need to be run in order by care must be taken when offsetting the management console ports since it may cause conflicts.

- [Installing WSO2 Application Server](#WSO2Server)
- [Installing WSO2 Enterprise Service Bus](#WSO2ESB)
- [Installing WSO2 Business Process Server](#WSO2BPS)
- [Installing WSO2 Developer Studio](#WSO2DS)
- [Installing TCP Mon](#TCPMON)
- [Installing Curl](#CURL)
- [Installing Apache ActiveMQ](#ACTIVEMQ)
- [Enabling JMS Transport Using Apache ActiveMQ](#ENABLEACTIVEMQ)

<a name="WSO2Server">Installing WSO2 Application Server</a>
----------------------------------
The application server is used for deploying and running any Java-based web application. It can be used to run a variety of web services including SOAP and RESTful services on different protocols (HTTP, JMS) and exchange data between them using (SOAP, POX (**Plain Old XML**), JSON).

1. In Windows, to start the application execute the "**wso2server.bat**", in OSX it should be "**wso2server.sh**".  
2. To open the management console the URL is - https://localhost:9443/carbon/
3. Default Username/Password for login is "**admin/admin**"
4. The server can be stopped by stopping in the command prompt or terminal.

There may be issues with starting the server if the JAVA_HOME environment variable is not set.

<a name="WSO2ESB">Installing WSO2 Enterprise Service Bus</a>
--------------------------------------
The WSO2 Enterprise Service Bus, is an open source ESB for enterprise application integration. An ESB is a model for designing and implementing communication between web services. 

If running the WS02 Application and WS02 ESB on the same machine, to allow their individual management consoles to be displayed, a the "**$ESB_HOME/repository/conf/carbon.xml**" file needs to be modified.

In the **carbon.xml**, change the <Offset> tag to **"\<Offset\>1\</Offset\>"** as this will change the port that the ESB console will be accessed (Port 9443 is default but will be used by WSO2 Application Server).

1. In Windows to start WS02 ESB, execute "**wso2server.bat**", in OSX it should be "**wso2server.sh**". Both files are located in the "**$ESB_HOME/bin**" folder.
2. To open the management console the URL is - https://localhost:9444/carbon/ (Port 9443 is reserved for the Application Server)
3. Default Username/Password for login is "**admin/admin**".
4. The server can be stopped by stopping in the command prompt or terminal.

<a name="WSO2BPS">Installing WSO2 Business Process Server</a>
---------------------------------------
The WSO2 Business Process Server (WSO2 BPS) is used for deploying and running executable business processes that are written in BPEL (Business Process Execution Language).

As with WSO2 ESB, if we are running WSO2 BPS on the same machine, we'll need to offset the port used for the management console. To do that we'll need to modifiy the "**$BPS_HOME/repository/conf/carbon.xml**". 

In the **carbon.xml**, change the <Offset> tag to **"\<Offset\>2\</Offset\>"** as this will change the port that the ESB console will be accessed (Port 9443 is used by WSO2 AS and Port 9444 is used by WSO2 ESB).

1. In Windows to start WS02 BPS, execute "**wso2server.bat**", in OSX it should be "**wso2server.sh**". Both files are located in the "**$BPS_HOME/bin**" folder.
2. To open the management console the URL is - https://localhost:9445/carbon/ (Port 9443 is reserved for the Application Server)
3. Default Username/Password for login is "**admin/admin**".
4. The server can be stopped by stopping in the command prompt or terminal.

<a name="WSO2DS">Installing WSO2 Developer Studio</a>
---------------------------------
The WSO2 Developer Studio is an Eclipsed-based IDE with some additional plugins to help with developing applications that will be deployed with WSO2.

If you want to develop under a specific JDK, the "**eclipse.ini**" will need to be modified in the $ECLIPSE_HOME directory. To do so just add the argument "**-vm $JVM**", where $JVM is the location of the desired virtual machine (**javaw.exe**).

Start the WSO2 Developer Studio and create a work space as per usual.

<a name="TCPMON">Installing TCPMon</a>
---------------------------------
TCPMon is a small utility that allows messages sent between clients and servers to be viewed and examined. It can be used to view HTTP/SOAP/XML/JSON messages that are exchanged between web service clients and web services

1. To run TCPMon, open the "**tcpmon.bat" file located in the "**$TCPMON_HOME/build**" directory.

<a name="CURL">Installing Curl</a>
--------------------------------
Curl is a utility to send requests to servers without having to write client code. It can be used to send HTTP messages to web services deployed on a WSO2 Application Server.

<a name="ACTIVEMQ">Installing Apache ActiveMQ</a>
--------------------------
Sometimes we'll need to enable JMS (Java Messaging Service) transport protocol with the WSO2 Application Server and/or ESB. Apache ActiveMQ is the middleware that supports JMS. The binary contains libraries (*.jar) files that can be added to projects.

<a name="ENABLEACTIVEMQ">Enabling JMS Transport Using Apache ActiveMQ</a>
--------------------------------------------
**This section is only to be enabled when required as it can cause conflicts with starting the various WSO2 servers**

Copy the following jars to **$AS_HOME/repository/components/lib** and **$ESB_HOME/repository/components/lib** directory.

- activemq-core-5.4.2.jar
- geronimo-j2ee-management_1.1_spec-1.0.1.jar
- geronimo-jms_1.1_spec-1.1.1.jar

Enable/Disable JMS Transport 
- Open the Axis2 configuration file in **$AS_HOME/repository/conf/axis2/axis2.xml** and **$ESB_HOME/repository/conf/axis2/axi2.xml**
- Uncomment the section **\<transportReceiver name="jms"\>** to **\</transportReceiver\>** that corresponds to ActiveMQ.
- Uncomment the section **\<transportSender name="jms"\>** to **\</transportSender\>** that corresponds to ActiveMQ.

To run ActiveMQ execute the **activemq.bat** file in **$ACTIVEMQ_HOME\bin.
