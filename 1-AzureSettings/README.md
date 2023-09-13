# First step (Azure Configuartions)

### Table of contents

* [Your Azure acount](#azure-account)
* [Resource Group](#resource-group)
* [Storage Acoount](#storage-account)

## Your Azure account
* Create your Azure account (if you new, you can get $300 free credits for new user, i'm using student account and get $100)

![](./1-AzureSettings/image/createaccount.png)

## Resource group
* Imaging Resource Group is just a logical store for your needed file for a specific project, so you can easily find, and interact with the file.

![](./1-AzureSettings/image/resourcegroup.png)


## Storage account
* Here is the physical store for your file(or resources). There plenty of settings in here, but tbh it quite easily to understand. Let's go through with me!
 -- WARNING: You should choose hiearachy namespace for easily access to your data like on you PC

![](./1-AzureSettings/image/storageaccount.png)

* There several things you have to pick here
 ** Region: You should pick where you at for the convenient and reduce delay time
 ** Performance: For this project you can go for standard (and i think most people use it)
 ** Redundancy: Where the data should be replicated at

![](./1-AzureSettings/image/storageaccount-register.png) --c