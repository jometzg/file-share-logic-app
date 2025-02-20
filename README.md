# File-Share Triggered Logic App Standard

This repo shows how a Logic App Standard can work with Windows file shares as a trigger.

## Logic Apps and File Shares
Azure Logic Apps has 2 different versions, the original Logic Apps Consumption (tier) and the newer Logic Apps Standard (tier) - which builds on the Azure App Services runtime. The differences are discussed [here](https://learn.microsoft.com/en-us/azure/logic-apps/single-tenant-overview-compare).

This repo will discuss Logic Apps Standard.

Besides the tier, there are different workflow [runtimes](https://learn.microsoft.com/en-us/azure/logic-apps/create-single-tenant-workflows-azure-portal#create-a-standard-logic-app-resource):
1. Workflow Service Plan
2. App Service Environment V3
3. Hybrid

The default is the *Workflow Service Plan*.

## File Shares
These are file shares hosted on a Windows Server environment. These are common in enterprises that use Windows Server. File and Storage Services on Windows Server allow the creation of *Shares* that may be used to trigger Logic App workflows.

![alt text](./images/file-share-windows-server.png "Windows Server File and Storage Services")

In the above, there is a file share that is called *fileshare* and is mapped to the folder on the server as *C:\\fileshare*

## Connecting to file shares
There are serveral ways in which a logic app may gain access to a file share:
1. if the file share is public, then no special measures are needed
2. if private and the Logic App is on the Workflow Service Plan, then a, [on-premise data gateway](https://learn.microsoft.com/en-us/data-integration/gateway/service-gateway-onprem) is needed. As of the time of writing in February 2025
3. if private and the Logic App is on an App Service Environment V3 (ASE), then the (ASE) naturally is on a virtual network and you may be able to route to the Windows Server that hosts the file server directly.

 > The above will be validated with the Logic App product group, but this is the understanding at this time.

## Installing the On-Premise Data Gateway
There are essentially 2 components to this gateway:
1. the agent that is installed on a virtual machine to manage this access. The default is to install this on the same VM as the Windows Server that hosts the file share.
2. An Azure component to which the gateway communicates.

## The VM installation
This requires an agent install to be downloaded to the Windows Server and installed with some Azure credentials that have access to the target Azure subscription.
Once installed it looks like this:

![alt text](./images/file-share-data-gateway-installed.png "On-premise data gateway installed on VM")

The Azure service looks like below:

![alt text](./images/file-share-data-gateway-azure.png "On-premise data gateway on Azure")

