Pipeline Creation and Learning
==============================

In this section, we show how to create a Pipeline and execute the Guided Learning approach
using the Falkonry Service. We start with a source data set that has several electromechanical 
points of measurement for a single power generator. Here is what the data looks like:

.. image:: ./images/motor_data.png

Create a Prediction Pipeline
----------------------------

First, the user creates an Event Buffer using this CSV file and a Condition Pipeline that 
consumes the event buffer data set to produce a condition assessment stream called Vibration.
Note that the pipeline does not contain multiple things. Also, the event buffer is set to
use the ISO 8601 timestamp format as explained in `Data Formatting <./dataformat.html>`_.

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168553121" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

Start Model Revision
--------------------

After creating the pipeline, the user instructs Falkonry to create a model revision from 
the data provided, and views the results.

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168553122" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

Since no verified condition examples were provided, the pipeline was able to identify five 
different conditions in the data and give them placeholder names.

Add Verification
----------------

The user examines the available maintenance or inspection logs and is able to verify some 
example conditions.  The user adds these example conditions to the pipeline.

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168709192" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

Learn some more
---------------

The user initiates another model revision that will incorporate the provided verified 
conditions.

The new results show labeled conditions across the whole time window.  At this point 
there are still a few conditions that are unrecognized and that maintain computer 
generated condition labels.

Live Monitoring and Continued Learning 
--------------------------------------

From the Configure tab, the user can choose to **Open Outflow**, in which case the most 
recent model revision is used to assess conditions in any existing or newly arriving data.

.. image:: ./images/pipeline_open.png

As soon as the user opens the outflow, live monitoring starts and assessments are produced
at the rate at which data arrives into the pipeline.  At any time, the user can initiate a
model revision and update the model used for live monitoring so that predictions can 
continue to improve.