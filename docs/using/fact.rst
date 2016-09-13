Verify
======

Condition facts (verified) examples are used by the Pipeline to apply meaningful names to 
conditions and to refine learning in order produce better condition recognition.

A condition fact is simply a condition value (a label) for a given time interval, for a 
given Entity that is known to the user to be the true condition of the given entity. 

Conditions facts can be added to the Pipeline in the following ways:

- File upload via UI or API
- Direct entry into Falkonry Service UI
- Use of a client application like the Falkonry Splunk App

File upload via UI or API
-------------------------

A set of condition facts can be added to a Pipeline through a simple CSV file.  The file 
must contain a header row with the fields, 'time', 'end', the Entity field name (which must 
match the field name supplied to the Pipeline at setup), and one or more Assessment names 
(matching Assessments already configured in the Pipeline).

The figure below shows an example file to upload a set of condition facts for the 
Assessment ``Health``.

.. image:: ./images/verification.png

For more details regarding how to format data files for use with Falkonry, please refer 
to `Data Formats <http://help.falkonry.com/en/latest/using/data.html#data-formats>`_.

In the Falkonry Service UI the Add Fact button (available on Learning and 
Outflow tabs) is used to view all previously entered facts and upload new facts 
contained in fact files. 

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168553120" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

Direct entry into Falkonry Service UI
-------------------------------------

Sometimes it is most convenient to add facts directly while viewing detailed 
assessment results for a specific Entity. For example, the user examines the available 
maintenance or inspection logs and is able to provide some condition facts. Users 
are directly able to add individual condition facts from the Entity detail view as 
shown in the figure below.  This dialog is invoked by clicking the Add Facts 
Example button.

.. raw:: html

   <iframe src="https://player.vimeo.com/video/168709192" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

Via a client application like the Splunk App
--------------------------------------------

Falkonry's Splunk App provides a direct way for users to add condition facts from within their 
Splunk user experience.  **Add Fact** is an available action for any Event Buffer 
visible on the **Data Exports** list.  Invoking that action produces a dialog shown in the figure 
below that lets a user create a set of condition facts from a Splunk search query.

.. image:: ./images/splunk_verification.png
