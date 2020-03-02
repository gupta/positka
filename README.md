# Positka: NSG Logs to Splunk 


The button below automates the process of deploying an Azure Function in your Azure account.
This Azure Function monitors the "NSG Flow Logs" and sends them to Splunk.


[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fgupta%2Fpositka%2Fmaster%2Fazuredeploy.json)


## Settings

The Function needs the following parameters to operate properly:

* Function Hosting Plan Type                     - "Consumption" or "Premium". 
   The Function can be hosted either on a Consumption plan or on a Premium Plan. For details refer: 
   [Azure Functions scale and hosting](https://docs.microsoft.com/en-us/azure/azure-functions/functions-scale)
* Premium Hosting Instance Size              - "EP1", "EP2", or "EP3".  
   If you select "Premium", then this setting determines the size of the instances. For details refer: 
   [Azure Functions Premium plan](https://docs.microsoft.com/en-us/azure/azure-functions/functions-premium-plan)  
* NSG Source Account          - the connection string of the storage account having the NSG log flows.  
   Example: ```DefaultEndpointsProtocol=https;AccountName=yyy;AccountKey=xxx;EndpointSuffix=core.windows.net```  
* Splunk HEC Address               - internet address of the Splunk HEC port.  
   Example: ```http://splunk_ip_address:8088/services/collector/event```  
* Splunk HEC Token                 - guid security token for Splunk HEC  
   Example: ```a77fdc21-0861-4d8b-941c-e1b4c556b4fb```

## Resources Deployed

The following resources are deployed:

| Name                     |  Type                |
|--------------------------|----------------------|
| NsgToSplunk              | App Service          |
| NsgSplunk-Hp-xxxxxxxxxx  | App Service Plan     |
| NsgSplunk-Ins-xxxxxxxxxx | Application Insights |
| nsgsplunkxxxxxxxxxxxxxx  | Storage Account      | 

The xxx... is a unique string composed using the subscription ID and the resource group ID.

## Billing

Kindly note that the resources deployed above are chargeable and the cost for these will be added by Microsoft to your Azure billing.

## Deployment Errors
In case of any deployment errors:
* Note down the details of the errors from "Notifications".
* Delete the resources created (to avoid billing)
* Contact Positka

## Operational Errors
In case of any operational errors:
* Note down the details of the errors from the Application Insights Service.
* Contact Positka.