Concepts & Overview
===================

The Falkonry Pattern Recognition System is used to extract a real-time understanding of condition from patterns in time series data. The most common use of the Falkonry Service is to provide intelligence to applications that are monitoring the condition of a complex system (e.g. an industrial machine, a set of devices, groups of people, etc.).

.. image:: images/operations_mgmt_solution.png

The Falkonry System is targeted for use by subject matter experts (SMEs). It is not a machine learning toolkit for data scientists.  Users of the service simply supply it with signal data and any available condition facts, and it will learn to recognize conditions.  Once it learns conditions, it will recognize those conditions in new data.  As it accumulates data and additional condition facts, it continues to learn and improve its ability to recognize or ‘assess’ conditions.

Entities
------

Entities are what they sound like - anything (e.g. an appliance, a device, a vehicle, a 
machine, a person) that produce a stream of data through its operation.

Signals
-------

Time series data is represented in the Falkonry Service as a set of Signals. Each Signal represents a sequence of values over time that can be indexed by Entity.  Signals can carry either numerical or categorical values.

Conditions
----------

Conditions are what we are trying to extract from patterns found in time series data. This is typically a measure of the state of some Entity. Conditions could be used to represent health, operating mode, risk or threat level, quality level, or almost any form of condition assessment. 

Falkonry can also recognize two other conditions - *Unknown* and *Gap*.

**Unknown**

While a pipeline is monitoring the inflow or merely running a test revision, any new patterns that arise which were not seen when the pipeline was learning will be reported as the unknown condition. An unknown condition is displayed on the timeline alongside other condition labels. 

If a fact is added about that pattern, then Falkonry learns from it and replaces the unknown condition with the provided fact.

**Gap**

Ordinarily unevenly sampled data is automatically handled in Falkonry. However, if there is long period of time during which any of the input signals has no data samples, then the assessment for such a period is reported as a gap condition and it is displayed on the UI with other assessment condition labels after learning. 

Facts
-----------------------

A fact is a known condition for a particular episode of time.  Facts can come from external sources, inspection reports, or investigations.  Facts data typically becomes available after events have passed.

Learning and Models
-------------------

The Falkonry Service is able to *Learn* a condition model from signal data and any condition facts.  The Falkonry Service is able to perform unsupervised, semi-supervised, and supervised learning on the supplied data to create a condition model.  When no condition facts are present, the model will recognize conditions and assign machine generated names. Facts aid learning, but there is no minimum numbers of facts that need to be supplied.  The Falkonry Service uses a continuous learning approach where models are revised over time as more signal data and facts are received.

Assessment
-----------

The application of a model to signal data to produce a condition assessment is called recognition. The Falkonry Service supports real-time condition recognition on signal data.

Datastreams
----------

A *Datastream* is the basic building block for pattern recognition used in Falkonry. A Datastream is associated with a set of *Signals* (that it consumes as input), a set of *Entities*, and a set of *Assessments* that convey the output of the Datastream.

A Datastream can consume a *History Window* of signal data and *Facts* that lie within the window to facilitate the learning of *Models*.

At any time one model can be designated as "Active". If the Datastream is turned on with an active model, signal data streamed into the Datastreams will produce a live output stream of assessment results.
