# Module 3: Using your on-premises StorageZone



## Test your StorageZone by uploading to a Shared Folder

With ShareFile it is possible to leverage more than a single StorageZone on an account, allowing customers to store their data in multiple on-prem zones, cloud zones, Citrix-managed zones or some combination thereof. 

To assign your newly created StorageZone to a Shared Folder first log into your ShareFile account, then navigate to _Folders > Shared Folders_. Click the green circle at the top right of the page and select **Create Folder**.

In the dialogue, name your folder and then select your private zone from the *StorageZone dropdown menu*.

Once in your folder drag to upload a file or two.

![Creating a shared folder](images/shared-folder.gif)

## Create a network file share Connector

Navigate to *Settings > Admin Settings > Connectors*. Browse to *Add Connectors* at the bottom of the page and find *Network Share*. Click the **Add** button.

Give your Connector a name and then enter the UNC path to a network file share in your environment.

![](images/create-connector.gif)
 
Test the Connector by browsing to *Folders > Network Shares* and clicking on your new test share. Authenticate with the domain credentials for a user account that has rights on the share.
 
![](images/connector-auth.gif)

## Conclusion

Congratulations! You have successfully configured an on-premises StorageZone and secured it with NetScaler. For additional technical documentation please check out [ShareFile Citrix Docs](https://docs.citrix.com/en-us/sharefile.html) where you can learn to automate user provisioning and configure SSO/SAML.

## Shortcuts

1. [Introduction: Deploying an on-premises StorageZones Controller](../)
2. [Module 1: Installing and Configuring an on-premises ShareFile StorageZone](../Module-1)
3. [Module 2: Configuring NetScaler for an on-premises ShareFile StorageZone](../Module-2)
4. Module 3: Using your on-premises StorageZone
