``POST /eventBuffer/``
======================

In order to create an event buffer all that is needed is the specification of the time
identifier and format of the values of timestamps used in the event buffer. Let’s take a 
closer look at that JSON definition.  Here are the first few lines for review:

:: 

  "sourceId": "some-external-id",
  "name": "APIEventBuffer",
  "timeIdentifier": "time",
  "timeFormat": "ISO8601",

=================== =========   ==================================================================================================
Property            Data type   Description
=================== =========   ==================================================================================================
``sourceId``        string      An identifier used in an external system to identify this event buffer
``name``            string*     An identifying name for the event buffer. It must be  unique for the account and may be changed later.  
``timeIdentifier``  string*     The column in the input data which represents timestamps for each event
``timeFormat``      string*     The format of the timestamps for each event in the input data
=================== =========   ==================================================================================================

Here is some sample code for invoking the event buffer creation API:

.. code-block:: javascript

    var unirest = require('unirest');
    var fs = require('fs');

    var myEventBufferId = null;
    var myToken = "m9v8pxfykd24bz";

    var url = "https://service.falkonry.io/eventBuffer";
    var myFile = "./createPipeline.json";

    var Request = unirest.post(url)
      .type('json')
      .headers({
        'Authorization': 'Token ' + myToken,
        'Accept': 'application/json'
      }).send({
        "name": "My pipeline",
        "sourceId": "An external identifier",
        "timeIdentifier": "time",
        "timeFormat": "ISO8601"
      })
      .end(function (response) {
         myEventBufferId = response.id;
         //add error handling here
         console.log(response.status);
         console.log(response.body);
    })

The value of ``myToken`` will vary for your implementation.
