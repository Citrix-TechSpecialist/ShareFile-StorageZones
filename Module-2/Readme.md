# Module 2: Configuring NetScaler for an on-premises ShareFile StorageZone

Configuring the NetScaler to manage and secure ShareFile traffic is made fairly straightforward with the ShareFile Wizard.

The chart below outlines the five features that ShareFile leverages NetScaler for managing traffic to a StorageZone, including their availability by NetScaler Edition.


|                   | Platinum Edition | Enterprise Edition | Standard Edition |
| :---              | :---:            | :---:              | :---:            |
| Load Balancing		| •                | •                  | •                |
| Responder Policy	| •                | •                  | •                |
| HTTP Callouts		| •                | •                  | •                |
| Content Switching | •                | •                  |                  |
| AAA					| •                | •                  |                  |

Content Switching and AAA are required to authenticate inbound user requests to StorageZone Connectors at the NetScaler before passing the request on to the internal network -- otherwise authentication traffic will be passed to the StorageZone 

## Run the ShareFile Wizard
Log into the NetScaler management interface and navigate to the Configuration tab. Click on the **Traffic Management** section and select **Setup NetScaler for ShareFile**.

When asked to enter a *public IP address and a name for the content switching virtual server* enter the public IP address or DMZ IP address which will be the ingress point at the NetScaler for ShareFile StorageZone requests. you may leave the default name if you wish. 

Check the box for **StorageZones Connector for network file shares and SharePoint**. Click **Continue**. 

![start ShareFile wizard](images/sfwizard-csip.gif)

In the *Certificates* section select or install the required public SSL certificate for the StorageZone.

![ShareFile wizard certificate](images/sfwizard-cert.gif)

In the *ShareFile StorageZone Controller Configuration* section click on **Add New StorageZone Controller**. Enter the IP address for your StorageZone Controller host machine.

Select whether you would like the NetScaler to pass internal traffic between itself and the StorageZone Controllers encrypted (https over 443) or unencrypted (https over 443).

If you are encrypting traffic from the NetScaler to the StorageZone Controller you must have the SSL certificate installed on the StorageZone Controller and bound on 443 in IIS.

![ShareFile wizard certificate](images/sfwizard-server.gif)

Next create an LDAP configuration so user StorageZones Connector requests to a **AAA Virtual Server IP Address** can be authenticated. The *AAA virtual server IP address* should *not* be in use elsewhere in your environment.

![ShareFile wizard AAA](images/sfwizard-aaa.gif)

Finalize the configuration.

## Add support for browsing Connectors from the web

To support web access to StorageZone Connectors, you must perform additional NetScaler configuration after you complete the NetScaler for ShareFile wizard.

In this section you will create and configure a third NetScaler load-balancing virtual server, used to ensure that ShareFile clients send credentials only when logged on to a trusted ShareFile domain.

StorageZones Controller uses the Cross-Origin Resource Sharing (CORS) standard to provide the necessary security for requests to restricted zones and from the ShareFile web interface to StorageZone Connectors. CORS uses HTTP headers to allow the client and server to know enough about each other to determine if a request or response should succeed.

Navigate to *Load Balancing > Virtual Servers* and click **Add** to create a new LB VIP.

Name the LB VIP something like **SF_OPTIONS**. Set the **Protocol** to *SSL*. Set the **IP Address Type** to *Non Addressable*.

Bind the exisitng *SF_SVC* service and the *SSL certificate* to your *SF_OPTIONS* LB VIP.

![Configure Options LB VIP](images/sfoptions-lb.gif)

Navigate to 






