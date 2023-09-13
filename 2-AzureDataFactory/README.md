# Second step (Azure Datafactory)

### Table of contents

* [Your Azure DataFactory](#azure-df)
* [DataFactory configuration](DataFactory-configuration)
* [Lauch DataFactory](#Lauch-DataFactory)
* [Create your first pipeline](#first-pipeline)
* [Create stage in your pipeline](#phase-pipeline)

## Your Azure DataFactory
* Create your Azure DataFactory, this is where you create and monitor your pipeline.

![](/2-AzureDataFactory/Azure-DataFactory.png)

## Azure DataFactory configuration
* You can pick default all the options and continue.

![](/2-AzureDataFactory/createADF.png)


## Lauch DataFactory
* Click on the DataFactory, and launch it, it will take you to another page, where Azure provide an UI for easily interact with the pipeline

![](/2-AzureDataFactory/launchADF.png)


## Create your first pipeline
* Create your first pipeline here!

![](/2-AzureDataFactory/createPipelineADF.png)

## Create your pipeline phase
* Set your stage like this, don't worry i will help you to define some settings of each.

![](/2-AzureDataFactory/pipelineElement.png)

* First the Get Metadata stage, in the setting part, you mount your Get metadata stage to each file store on the Blob Storage (here we have typicall 4 files with the pre-defined schema)

![](/2-AzureDataFactory/getmetadata.png)

* Next, the If scheme matches stage, you set up the expression with this logical syntax to compare the schema of the files

    ** @and(equals(activity('Movie Schema').output.structure,activity('Movie File').output.structure),equals(activity('Ratings File').output.structure,activity('Ratings Schema').output.structure)) 

    -- In the If true activity we send the Successful File data to Azure Databricks notebook for computing

    -- In the If False activity we send back the Failed file to Sink, which is rejected file we created in Blob storage
![](/2-AzureDataFactory/if.png)
![](/2-AzureDataFactory/iftrue.png)
# Create Azure Logic App

* We need to create the Azure Logic App for the last stage of the ADF pipeline, this typically invole when the If true stage send the data file to the Azure DataBricks for computing, we need to take the result back, and the result have to in structure we denfine


* Warning: We have to mount the URL of the last stage which is Web: Success and Fail Email to the URL of the Azure Logic App

* The code from the HTTP request is received 
<br>
 {
    "properties": {
        "DataFactoryName": {
            "type": "string"
        },
        "EmailTo": {
            "type": "string"
        },
        "ErrorMessage": {
            "type": "string"
        },
        "PipelineName": {
            "type": "string"
        },
        "Subject": {
            "type": "string"
        }
    },
    "type": "object"
}

![](/2-AzureDataFactory/LogicApp.png)

