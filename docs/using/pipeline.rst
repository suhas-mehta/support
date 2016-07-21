Pipeline Creation
=================

In order to create a pipeline, the user must select an event buffer. Multiple pipelines can share the same event buffer. After the event buffer is selected Falkonry will display the signals it analyzed.

.. image:: ./images/pipelineSignals.png

Falkonry displays the characteristics of each signal it identifys and allows the user to **use** or **ignore** any of the sensors in the data. In the Human Activity data example, all the signals are numerical samples.

.. image:: ./images/createPipeline.png

Falkonry asks what is being accessed, in the case of the Human Activity example, it is what activity is being performed. Then it asks for the Time Window Guidance. In most cases the default of 1 second is appropriate.

