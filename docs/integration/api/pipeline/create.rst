``POST /pipeline/``
===================

For the sake of completeness, let’s take another look at the create pipeline API.   

Earlier in this document, we created the pipeline using the Interactive API Web page.  We 
copied and pasted the JSON definition of the pipeline into that Web page.  Let’s take a 
closer look at that JSON definition.  Here are the first few lines for review:

:: 

  "sourceId": "sourcename",
  "name": "APITestPipeline",
  "input": "3ykf2jjfr6gvgd",
  "entityIdentifier": "person",

==================== =========   ==================================================================================================
Property             Data type   Description
==================== =========   ==================================================================================================
``sourceId``         string      An identifier used in an external system to identify this pipeline
``name``             string      An identifying name for the pipeline. It must be  unique for the account and may be changed later.  
``input``            string      The identifier of the event buffer used to supply inflow to this pipeline
``entityIdentifier`` string      The column in the input data which identifies each individual entity in the pipeline. 
==================== =========   ==================================================================================================


The list of signals referenced in the pipeline is defined along with their
name, value, and event types. 

The ``name`` of a signal is the column header value in the case of a CSV file or the
key part of an name/value pair in a JSON file used for the input data of a pipeline.

The ``valueType`` of a signal is the data format used for conveying values as either
``Numeric`` or ``Categorical``. In the case of ``Categorical`` values, the values are to
be interpreted as strings or text, whereas ``Numeric`` values are interpreted as real 
numbers.

The ``eventType`` of a signal is indicative of whether the 
value has an analog or a discrete source. The ``Samples`` type indicates that the signal 
has been sampled at a convenient rate and that more values are present between events that 
were simply not sampled. Its opposite is the ``Occurrences`` type, which indicates that 
every moment in time for which the signal could be sampled has been recorded and that there 
is no other value possible for other timestamps.

::

  "inputList": [
    {
       "name": "T_xacc",
        "valueType": {
          "type": "Numeric"
      },
      "eventType": {
        "type": "Samples"
        }
    },
    {
        "name": "T_yacc",
        "valueType": {
          "type": "Numeric"
        }
      },
      "eventType": {
        "type": "Samples"
    }],


And further down in the file we find the list of assessments desired from the pipeline.
The definition of an assessment simply references the list of input signals that are used
by Falkonry service to produce the assessment. Note that the list of inputs can be 
altered during the lifetime of a pipeline. However, the name of an assessment cannot be
changed once a revision is created.

The a priori conditions are listed to provide options for the facts
used in the pipeline for the given assessment. Values can be arbitrary text and no
duplicate values should be used.

:: 

  "assessmentList": [
    {
      "name": "Activity",
      "inputList": [
         "T_xacc",
          "T_yacc",
          "T_zacc",
          "RA_xacc",
          "RA_yacc",
          "RA_zacc",
          "LA_xacc",
          "LA_yacc",
          "LA_zacc",
          "RL_xacc",
          "RL_yacc",
          "RL_zacc",
          "LL_xacc",
          "LL_yacc",
          "LL_zacc"
      ],
      "aprioriConditionList": [
        "Walking"
      ]
    },


Another important option to specify is the minimum frequency at which assessment results are 
desired for the pipeline. This frequency can either be specified as a fixed interval or
as a grouping signal that references a categorical input. If left undefined, it is assumed
to mean that desired frequency is once a second or upon the dominant interval whichever is
higher.

:: 

  "interval": {
    "duration": "PT1S"
  }

The ISO 8601 formatted interval here specifies that an assessment is desired every second.

:: 

  "interval": {
    "field": "capture_id"
  }

The example here defines the assessment interval to be as often as the value of the 
categorical field ``capture_id`` changes. This provides the user to control the rate at
which assessments are produced.

:: 

  "interval": {
  }

This option allows Falkonry Service to determine the rate at which assessments are to be
produced.

An easy way to get a start on your JSON file would be to create a pipeline manually in the 
Falkonry Service UI using your data set.  Then do a ``GET /pipeline/{id}`` to get the JSON 
definition of that pipeline.  

Here is some sample code for invoking the pipeline creation API:

.. code-block:: javascript

    var unirest = require('unirest');
    var fs = require('fs');

    var myPipelineId = null;
    var myToken = "m9v8pxfykd24bz";

    var url = "https://service.falkonry.io/pipeline";
    var myFile = "./createPipeline.json";

    var myData = JSON.parse(fs.readFileSync(myFile))  //add error handling here

    var Request = unirest.post(url)
      .type('json')
      .headers({
        'Authorization': 'Token ' + myToken,
        'Accept': 'application/json'
      }).send(myData)
      .end(function (response) {
         myPipelineId = response.id;
         //add error handling here
         console.log(response.status);
         console.log(response.body);
    })

The value of ``myToken`` will vary for your implementation.

