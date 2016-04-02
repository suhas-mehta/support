Pipeline REST API
==================

Most likely you will want to use the API programmatically from within an application.  
This section gives example API calls using Javascript and Node.js, and utilizing the 
``unirest`` node.js module. For detailed information on using Node.js please visit 
https://nodejs.org/en/. For detailed information on using the ``unirest`` library 
please visit http://unirest.io/nodejs.html.  Please note these examples are intended as 
a simple starting point, not fully robust code.  At a minimum you will need to add error 
handling.

**Falkonry Pipeline Lifecycle using the API**

The following outlines a typical lifecycle of a pipeline created through the API.  Each of 
the steps represents a calling an API function.

 1. Pipeline (create) - This sets up an empty pipeline and names the input signals, things, 
    and assessments.
 2. Pipeline input - Load input signal data into a pipeline. The names of the signals and 
    things must match what was set up in the create pipeline step.
 3. Pipeline reviseModel - This initiates a learning cycle and generates the first or a new 
    version of the model.
 4. Pipeline verification - Adds verification data to the pipeline.  The column names of the 
    verification data must match the things and assessments used in the pipeline creation.
 5. Pipeline open - Promotes the pipeline to live state.  Pipeline will generate outflow 
    assessment data based on the input data it receives.
 6. Pipeline input - Add additional input signal data, possibly live data.
 7. Pipeline output - Retrieve the condition assessment data produced by the pipeline.  
 8. Repeat: verification, reviseModel, open, close, input, output as needed.

.. toctree::
   :maxdepth: 1
   
   new
   input
   revise
   verification
   open
   output
   create
