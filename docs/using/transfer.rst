Transferring Data
=================

There are three methods by which Source Signal Data can be provided to a Falkonry Pipeline:

- File upload via `Falkonry Service UI <./pipeline.html>`_ 
- Through a programmatic client using `Falkonry API <../connector/index.html>`_
- Through an MQTT broker using `event buffer subscriptions <../connector/index.html>`_
- Client application - like the `Falkonry Splunk App <../splunk_app/index.html>`_

File upload via Falkonry Service UI or API
------------------------------------------
During Pipeline creation, Falkonry will ask the user to upload a CSV file containing 
Source Signal data.  The file can be uploaded by either dropping the file on the UI or by 
navigating to and selecting the file in the file system. Falkonry will use this starting 
source data to begin the model creation.   Additionally, more input data can be added to 
the pipeline using a similar mechanism once the pipeline is live.  The data must be in a 
specific format.

The following figure shows part of a file in the appropriate structure.  The Thing field 
is named ``unit``, and we have four signals ``voltage``, ``current``, ``rpm``, and ``vibration``.

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168575780" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

The four signals above were all of the *Numerical* type.  Falkonry supports two types of 
source signals:

- Numerical: scalar value of any type of number
- Categorical: a label that can one of a set of options, represented with a string

More details regarding supported data formats such as CSV and JSON files can be found here_.

.. _here: dataformat.html

Event Buffer subscription to MQTT broker
----------------------------------------

When a continuous stream of data is required for a pipeline, the data can be delivered to
Falkonry either through its `Event Buffer REST API <../connector/api/buffer/index.html>`
or through subscription of the event buffer to an MQTT broker. 

Simple properties of the subscription are specified when the MQTT broker is configured,
such as its URL, user name, and password. Falkonry treats the data transmission just like
if individual files are created.

Once a subscription is created, the event buffer will keep receiving 

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168680003" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

Sending data via a Client application like the Splunk App 
---------------------------------------------------------

A client application like the Splunk App allows a user to work with data in a familiar 
context and to use the app to send data to the Falkonry Service. 

.. image:: ./images/splunk.png

With the Splunk App, a user gathers the source signal data they need through a standard 
search query.  The figure below shows the display of such a search in the Splunk App. Once
the data has been located, the user creates an event buffer in the App and then uses the
event buffer in the Falkonry Service to create pipelines.

.. image:: ./images/splunk_export.png
