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

 1. `Pipeline (create) <create.html>`_ - This sets up an empty pipeline and names the input 
    signals, entities, and assessments.
 2. `Event Buffer input <../buffer/input.html>`_- Load input signal data into the pipeline's
    event buffer. The names of the signals and entities must match what was set up in the 
    create pipeline step.
 3. `Pipeline reviseModel <revise.html>`_ - This initiates a learning cycle and generates 
    the first or a new version of the model.
 4. `Pipeline facts <verification.html>`_ - Adds facts data to the pipeline.  
    The column names of the facts data must match the entities and assessments used 
    in the pipeline creation.
 5. `Pipeline open <open.html>`_ - Promotes the pipeline to live state.  Pipeline will 
    generate outflow assessment data based on the input data it receives.
 6. `Event Buffer input <../buffer/input.html>`_ - Add additional input signal data, 
    possibly live data.
 7. `Pipeline output <output.html>`_ - Retrieve the condition assessment data produced by 
    the pipeline.  
 8. Repeat: add facts, reviseModel, open, close, input, output as needed.

.. toctree::
   :maxdepth: 1
   
   new
   revise
   add facts
   open
   output
   create
