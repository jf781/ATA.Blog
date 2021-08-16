# Introduction to Azure Arc

### What is Azure Arc

Our cloud providers today have given us a variety of tools to help manage the resources you have running within then.  The major vendors each have their own solutions to help us monitor, maintain security, and managing deployments in their ecosystem.  However, most of us have resources that are running on more than one cloud platform and on-premises.  Wouldn't it be great to have a way to manage those without having to learn another tool?

This is where Azure Arc can help fill that gap.  By allowing you to manage a resource regardless of which platform is hosting it.  Today we are going to focus on Azure Arc enabled servers.  


### Prerequisites

1. An Azure account (A free trial subscription will work)
2. A VM that is hosted outside of Azure (On-premises or in another cloud vendor) that has internet access.
3. The VM must be a [supported operating system](https://docs.microsoft.com/en-us/azure/azure-arc/servers/agent-overview#supported-operating-systems).
4. Administrator or root level access to that VM. 


### How it works

Azure Arc works by having an agent that runs on the resource.  When this agent is deployed, you specify some information about your Azure environment.  It will use this information to create a resource in your Azure subscriptions.   Once the resource shows up in Azure you now have a few different ways that you can manage it.  This can include installing extensions to gather logs, monitor its utilization, or to deploy a software on it.  Much the same as you can do to the resource as if it was running in Azure. 


### How to install the Azure Arc agent

Let's assume we have a VM running in VMware on-premises that we'd like to manage in Azure Arc.   The first thing we need to do is download and install the agent to that machine.  To do that let's go to our Azure Portal and search for Azure Arc and select "Servers - Azure Arc" from the list.  (We can see other Arc services listed but that will be for future blog posts). Then

![Search for Azure Arc](images/intro-001.png)

We will now select "Add" in the top left.   This will pull up a screen giving us a few different options on what type of installer we would like to use.   Since we are only doing a single VM this time we will select "Add a single server", but will keep this in mind for future deployments. 

(Picture time)

It will give us a list of prerequisites that were mentioned above.   On the "Resource details" page it will give a chance to determine where the resource is represented in Azure as well as the operating system type.   We are using Windows for our example and will use the details below for the subscription and resource group.  

(More picture time)

We can now define tags on it just like we would about any other resource in Azure.  It even pre-populates some tags that can be helpful to identify a resource that isn't hosted within Azure like "City", "Datacenter".   

(You guessed it, more pictures)

We now have a chance to view the script that we need to run our VM.   You can see the script will download and install the AzureConnectedMachineAgent.msi file.  It will then provide the information we specified when the agent connects to Azure.

(Pictures everywhere)

After we run the script on the VM, we will get a message telling us to navigate to Azure to see the machine.   After a few minutes, we can now see our Arc enabled server running in the portal. 


### Conclusion

Azure Arc is a great way for us to manage multiple resource types from Azure in a centralized and consolidated manner.  This in itself is nice but not super exciting.  As you start incorporating other Azure tools, like Sentinel and Azure Policy, you start to fully see the power that Azure Arc provides.  You could be so daring as to use the "Single pane of glass" phrase that gets thrown around excessively.   In this instance though, I feel it is fully justifiable.  