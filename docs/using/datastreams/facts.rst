Facts Data File Format
======================


Facts data is used to provide feedback to the Falkonry learning process in order to 
supply condition names as well as to fine tune its findings. 

Continuous (Sliding) Windows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The facts data must contain a time column (for the interval start), an end column (for the internal end), 
an optional entity identifier, followed by one condition label. When uploading facts, either using the Falkonry 
Application Development Kit (ADK) or the Falkonry LRS UI, user can provide header identifiers for each of these fields.
For example, facts data used for the Wheel Health data contains the following header::

  start, end, wheel, Wheel_health

It is possible to provide more than one assessment in the facts data set. Moreover, the values for the assessment are the 
names of condition that are desired to be used in the assessment. For example, the following data from another data set conveys 
four different condition facts

**CSV**::

  time,end,unit,Reliability
  2015-04-22T19:54:02Z,2015-04-22T19:54:04.750Z,PM-6428,Base
  2015-04-22T19:54:05Z,2015-04-22T19:54:06Z,PM-6428,Production
  2015-04-22T19:54:10Z,2015-04-22T19:54:11Z,PM-6428,Production
  2015-04-22T19:54:30Z,2015-04-22T19:54:35Z,PM-6428,Dead Sensor

**JSON**

In line-delimited JSON, this data would appear like the following::

  {"time": "2015-04-22T19:54:02Z", "unit": "machine1", "end": "2015-04-22T19:54:04.750Z", "Reliability": "Base"}
  {"time": "2015-04-22T19:54:05Z", "unit": "machine1", "end": "2015-04-22T19:54:06Z", "Reliability": "Production"}
  {"time": "2015-04-22T19:54:10Z", "unit": "machine1", "end": "2015-04-22T19:54:11Z", "Reliability": "Production"}
  {"time": "2015-04-22T19:54:30Z", "unit": "machine1", "end": "2015-04-22T19:54:35Z", "Reliability": "Dead Sensor"}



Batch Windows
^^^^^^^^^^^^^^^

In the case of a Batch Windows datastream, facts can either be time-marked or indexed with a batch identifier.
For time-marked fact rows the format is exactly the same as *Sliding Windows*.

Note: A datastream is classified as Batch as against Sliding during datastream creation itself. Identifying a batch identifier during datastream creation marks the datastream as Batch going forward.

For facts that are indexed using batch identifiers, replace start/end time segments with the batch identifier field. For example, in a batch testcase, facts would look like:


**CSV**::

  batch_id,unit,machine_state
  1,machine1,normal
  2,machine1,normal
  3,machine1,warning
  4,machine1,failure

**JSON**

In line-delimited JSON, this data would appear like the following::

  {"batch_id": "1", "unit": "PM-6428", "machine_state": "normal"}
  {"batch_id": "2", "unit": "PM-6428", "machine_state": "normal"}
  {"batch_id": "3", "unit": "PM-6428", "machine_state": "warning"}
  {"batch_id": "4", "unit": "PM-6428", "machine_state": "failure"}


  
Output data
~~~~~~~~~~~

Output data can be retrieved from a Falkonry assessment using its API, or exported manually 
through the Falkonry UI. The main purpose of this output data is to be 
able to view all the assessments for every entity and timestamp. The output 
data contains one time column, zero or one entity identifier, one condition assessment and a batch_identfier 
in the case of batch datastreams.

For example, the output data of the sports activity example contains the following header::

  time, person, Activity

Note that both the entity identifier and the assessment identified in the header will match 
what was previously been set up in the assessment. Moreover, the values for the 
assessment are the names of conditions. For example, 
the following data is a snippet of the output from the sports activity assessment::

  time, person, Activity
  1474866318337, p1, Sitting
  1474866328417, p1, Sitting
  1474866318217, p1, Walking
  1474866328897, p1, Rowing
  
In line-delimited JSON, this data would appear like the following::  
  
  {"time": "1474866318337", "person": "p1", "Activity": "Sitting"}
  {"time": "1474866328417", "person": "p1", "Activity": "Sitting"}
  {"time": "1474866318217", "person": "p1", "Activity": "Walking"}
  {"time": "1474866328897", "person": "p1", "Activity": "Rowing"}


Note: For a batch datastream, there will be an additional column/ field for the batch identifier (in addition to the time field)
