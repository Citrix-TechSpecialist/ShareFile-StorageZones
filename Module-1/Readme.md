# Module 1: Installing and Configuring the StorageZone

When configuring an on-premises StorageZone it is best to first have all pre-requisites in place before starting the installation. The following is the pre-requisites list:

* A dedicated physical or virtual machine with 2 CPUs and 4 GB RAM
 * Windows Server 2016
 * Windows Server 2012 R2 (Datacenter, Standard, or Essentials)
 * Windows Server 2008 R2, 64-bit edition, SP1 (Datacenter, Standard, or Essentials)
* A publicy resolvable Fully Qualified Domain Name
* Enable SSL for communication with ShareFile
* A public SSL certificate
* Allow inbound TCP requests on 443 through your firewall
* Allow outbound TCP requests to the ShareFile Application on port 443 through your firewall

## Preparing your VM for StorageZones Controller 

1. Open a session to the Virtual Machine you will be using as your StorageZones Controller. 
2. Navigate to the [ShareFile downloads page](https://www.citrix.com/downloads/sharefile/) on the Citrix site and download the latest version of ShareFile StorageZones Controller to your VM.
3. Create a new file share and give Full Control to a dedicated ShareFile service account. This network share will be dedicated to ShareFile Data only and will not be directly accessible to users over the network. it's generally a good idea to host this file share on a file server
![docker-pull](images/create-sfdata-shared-folder.gif)
4. 


## Exercises 

Navigate to and complete the following exercises within **Module 1**.

1. [Pulling from Docker Hub](./Exercise-1)
2. [Running a Container](./Exercise-2)

# Reset the Sandbox Environment 

Once you have completed **Module 1**, reset the environment by typing in the following command in your sandbox environment: 

`sudo /dockerclean.sh`

If you are following along on your local machine, enter the following commands to remove all docker containers, images, and docker volumes from your host: 

```
docker kill $(docker ps -q)
docker rm -f $(docker ps -a -q)
docker rmi $(docker images -q)
docker volume rm $(docker volume ls -qf)
```

### Shortcuts

1. [Module 0-A: Install Docker Locally](https://hub.docker.com/?next=https%3A%2F%2Fhub.docker.com%2F)
2. [Module 0-B: Access your Docker Lab Development Box](../Module-0)
2. [Module 1: Running Docker Containers](../Module-1)
3. [Module 2: Creating Custom Images from Dockerfiles](../Module-2)
4. [Module 3: Using Docker Compose](../Module-3)
