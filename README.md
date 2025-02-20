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


