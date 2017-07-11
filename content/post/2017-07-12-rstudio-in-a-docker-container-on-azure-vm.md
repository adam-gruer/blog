---
title: RStudio in a docker container on Azure VM
author: 'Adam Gruer'
date: '2017-07-12'
slug: rstudio-in-a-docker-container-on-azure-vm
categories: []
tags: []
---

[link](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/dockerextension)

Using the Azure CLI 2.0
`az group create --name myDockerResourceGroup --location southeastaustralia`

Deploy a VM with the following vaariables:
newStorageAccountName: grueraDockerDisks
adminUsername: gruera
adminPassword: P@ssw0rd!
dnsNameForPublicIP: grueraDocker

`az group deployment create --resource-group myResourceGroup \
  --parameters '{"newStorageAccountName": {"value": "grueraDockerDisks"},
    "adminUsername": {"value": "gruera"},
    "adminPassword": {"value": "P@ssw0rd!"},
    "dnsNameForPublicIP": {"value": "grueraDocker"}}' \
  --template-uri https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/docker-simple-on-ubuntu/azuredeploy.json`


