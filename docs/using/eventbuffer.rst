Event Buffer Creation
=====================

File upload via Falkonry Service UI or API
------------------------------------------

We start with a source data set that has several electromechanical points of measurement for a 
single power generator. The following figure shows part of a file in the appropriate structure.  
The Thing field is named ``unit``, and we have four signals ``voltage``, ``current``, ``rpm``, 
and ``vibration``.


.. image:: ./images/motor_data.png

The four signals above are all of the *Numerical*  type.  Falkonry supports two types of 
source signals:

- Numerical: scalar value of any type of number
- Categorical: a label that can one of a set of options, represented with a string


First, the user creates an Event Buffer using this CSV file and a Condition Pipeline that 
consumes the event buffer data set to produce a condition assessment stream called Vibration.
During Event Buffer creation, Falkonry will ask the user to upload a CSV file containing 
Source Signal data.  The file can be uploaded by either dropping the file on the UI or by 
navigating to and selecting the file in the file system. Falkonry will use this starting 
source data to begin the model creation.  Additionally, more input data can be added to 
the pipeline using a similar mechanism once the pipeline is live. 

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168553121" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>


Note that the data does not contain multiple things and the event buffer is set to
use the ISO 8601 timestamp format. More details regarding supported data formats such 
as CSV and JSON files can be found in `Data Formats <http://help.falkonry.com/en/latest/using/data.html#data-formats>`_.



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
