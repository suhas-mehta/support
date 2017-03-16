Facts Data File Format
======================

**CSV**

Facts data is used to provide feedback to the Falkonry learning process in order to 
supply condition names as well as to fine tune its findings. The facts data must 
contain a time column (for the interval start), an end column (which must be called "end"), 
an optional entity identifier, followed by one condition label. The header of the CSV file 
should reflect the appropriate column names. For example, facts data used for the Wheel Health
data contains the following header::

  time, unit, end, L1 Wheel Health

Note that both the entity identifier and the assessment identified in the header must match 
what has previously been set up in the pipeline.  It is possible to provide more than one 
assessment in the facts data set. Moreover, the values for the assessment are the 
names of condition that are desired to be used in the pipeline. For example, the following 
data from another data set conveys four different condition facts::

  time,unit,end,Reliability
  2015-04-22T19:54:02Z,PM-6428,2015-04-22T19:54:04.750Z,Base
  2015-04-22T19:54:05Z,PM-6428,2015-04-22T19:54:06Z,Production
  2015-04-22T19:54:10Z,PM-6428,2015-04-22T19:54:11Z,Production
  2015-04-22T19:54:30Z,PM-6428,2015-04-22T19:54:35Z,Dead Sensor

**JSON**

In line-delimited JSON, this data would appear like the following::

  {"time": "2015-04-22T19:54:02Z", "unit": "PM-6428", "end": "2015-04-22T19:54:04.750Z", "Reliability": "Base"}
  {"time": "2015-04-22T19:54:05Z", "unit": "PM-6428", "end": "2015-04-22T19:54:06Z", "Reliability": "Production"}
  {"time": "2015-04-22T19:54:10Z", "unit": "PM-6428", "end": "2015-04-22T19:54:11Z", "Reliability": "Production"}
  {"time": "2015-04-22T19:54:30Z", "unit": "PM-6428", "end": "2015-04-22T19:54:35Z", "Reliability": "Dead Sensor"}
  
Output data
~~~~~~~~~~~

Output data can be retrieved from a Falkonry pipeline using its API, or exported manually 
through the Falkonry UI, on the Outflow tab. The main purpose of this output data is to be 
able to view all the assessments and estimates for every entity and timestamp. The output 
data contains one time column, zero or one entity identifier, and one condition assessment.  
For example, the output data of the sports activity example contains the following header::

  time, person, Activity

Note that both the entity identifier and the assessment identified in the header will match 
what was previously been set up in the pipeline.  If the pipeline produces more than one 
assessment, then each will be present in this data set. Moreover, the values for the 
assessment are the names of conditions that were produced by the pipeline. For example, 
the following data is a snippet of the output from the sports activity pipeline::

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
