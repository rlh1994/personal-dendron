---
id: AgkaBV4bzMI1bnX6p81UQ
title: Runtime Variables
desc: ''
updated: 1644444818444
created: 1644419342351
---


https://docs.streamsets.com/portal/transformer/latest/help/transformer/PipelineConfig/Runtime.htm 

# Runtime Parameters
Runtime parameters are parameters specific to a pipeline, they can have a default and can be overwritten when calling a pipeline (passed as arguments to it). These only exist within the context of the pipeline. 

## Define a Runtime Parameter
You define runtime parameters when you configure the pipeline; in the pipeline properties, click the Parameters tab and enter parameter names and default values in this tab.

![](/assets/images/2022-02-09-15-17-46.png)


## Call the Runtime Parameter
To use an expression in the pipeline you need to call a runtime parameter.You can use runtime parameters to represent any stage or pipeline property that allows the use of the StreamSets expression language, including properties that display as text boxes, checkboxes, or drop-down menus. You can also call a runtime parameter in the code developed for a scripting processor.

### Calling from Text Boxes
To call a runtime parameter in a stage or pipeline property that displays as a text box, use the following syntax:

`${<parameter name>}`

You can use a runtime parameter to represent a part of a property. For example, you could use a `RootDir` runtime parameter and append the rest of the directory in the property as follows:

`${RootDir}/logfiles`

### Calling from Checkboxes and Drop-Down Menus
To call a runtime parameter in a stage or pipeline property that displays as a checkbox or drop-down menu, you first must convert the property to a text box.

Click the Use Parameter icon (`<>`) next to the checkbox or drop-down menu to convert the property to a text box, and then call the parameter using the required syntax.

The parameter must evaluate to a valid option for the property type:
#### Checkboxes
Parameters called from properties that display as checkboxes must evaluate to true or false.

#### Drop-down menus
Parameters called from properties that display as drop-down menus must evaluate to a valid key value. Each option in the menu has an associated key value.

For example, to use a parameter for the Lookup Behavior property, the parameter must evaluate to one of the valid key values, such as `RETURN_ONE`, and not to the listed menu options, in this case, `Return first matching row`.

To view a valid key value, select the desired option from the menu, then click the **Use Parameter** icon. The text box displays the key value for the selected option. For example, after selecting the `Return a count of matching rows` option for the Lookup Behavior property, then clicking the Use Parameter icon, the text box displays `GET_COUNT` as the key value for that option.

### Calling from Scripting Processors
You can call a runtime parameter in the code developed for a scripting processor, such as the PySpark or Scala processors. Use the following syntax in any processor script:

`${<parameter name>}`

> Don't forget to include quotes if the value is a string.

![](/assets/images/2022-02-09-18-12-55.png)

## Start the Pipeline with Parameters
When you start the pipeline, you can specify the values to use for the parameters. From the pipeline canvas, click the Start menu, and then click Start with Parameters; the Start with Parameters dialog box lists all parameters defined for the pipeline and their default values. If Start with Parameters is not enabled, the pipeline is not valid. You can then override any default values with the values you want to use for this pipeline run, and click Start.

> If you want to use the parameter values defined in the pipeline, you can simply click the Start icon to start the pipeline.

# Record Value Runtime Variables
> This feature is only available within StreamSets Collector and is? not usable within a transformer pipeline. 

If you want to pass the value of a column from a query input as parameters to a later part of a pipeline you can use the following syntax:

`${record:value('/<column name>')}`

where the column name is case sensitive. 

## Calling jobs 
### Single record job calls
The common use for this is to pass these parameters to a job, which can be done using the following format within the `Start Job` processor:

```code
[{
    "<paramerter 1>":"${record:value('/<column 1>')}",
    "<paramerter 2>":${record:value('/<column 2>')}
}]
```

where the first value is in quotes as it is a string. This allows you to pass a single record to a job's parameters and run that job once.

### Job Templates
If you want to call the same job multiple times with different parameters then you need to ensure that you use a `Job Template` rather than a job. This is a tick box in the job configuration and otherwise acts the same, but allows multiples of the same job to be run at the same time with different inputs. The syntax is the same as above when the values you wish to use are from the same source, otherwise you can use the below for specifying different parameter sources.

```code
[
   {
      "<param1>": <param numeric value>,
      "<param2>": "<param string value>"
   }
   {
      "<param1>": <param numeric value>,
      "<param2>": "<param string value>"
   }
]
```
This is particularly useful when you want to implement a loop over some set of data, you first select the _loop_ table via a query from some source (ideally BQ for future reliability) and then start a job with each set of parameter values.

![](/assets/images/2022-02-09-18-11-31.png)
