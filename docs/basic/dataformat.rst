Formatting data
===============

The currently supported data format for exchange with Falkonry is CSV (comma separated values). 
This commonly used general purpose data exchange format allows you to use numerical, 
categorical, timestamp, and other types of data.  CSV files can be used to supply Input 
data (source signals) as well as verification data to Falkonry.

The first line of any CSV file will contain one line of "header" data which labels the 
data that follows.  This header data is analogous to the row of column names in a 
spreadsheet.  Each name or label will be separated by a comma.  For example, data used in 
the Turbofan example contains the following header::

  time, unit, T20_1, Nfc_1, SmLPC_1

The remaining rows in the CSV file will contain the data records.  Each line in the file 
will represent one record, and will contain a value for each of the labels defined in the 
header row.

Falkonry CSV requirements
-------------------------

CSV files for use with Falkonry have a few specific requirements.  Every CSV must have a 
timestamp column. Additionally, all the values used in the CSV file must have the same 
structure, i.e., the same set of attributes and their data types. Also, the file may 
contain UTF-8 characters, which is the encoding used for supplying data to Falkonry. 

Identifying time
----------------

In Falkonry, every record is used to convey data for a single instant or interval of time. 
Therefore, timestamps must be present on every record provided to Falkonry, which also 
means that your CSV file must have a column representing the timestamp. Within your CSV 
file the naming of the timestamp column is flexible; the time column will be identified 
during pipeline creation.

Your timestamp data can be specified using one of the following formats:

- ISO 8601 format. As you can see in this primer on the time format, you can identify timezones, sub-second precision, as well as the regular components on date and time.
- As a Unix-style long integer encoded as the number of milliseconds since Jan 1, 1970.
- 12/19/2014 11:22:00 or ``MM/DD/YYYY HH:mm:ss``
- 2015-02-03 12:55:03 or ``YYYY-MM-DD HH:mm:ss``
- Any timestamp format that can be described using `Java SimpleDateFormat 
  <https://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html>`_

When supplying verification data, you must also supply a second time column called end. 
This column is used to mark the end of the interval for which the record provides values.

Identifying things
------------------

Often your Falkonry data will correspond to more than one "thing".  You may have several 
turbofan motors that you are monitoring, or you may be collecting activity data from many 
people. If you have data for multiple things, you must have a column of data which represents 
your thing identifier.  The column that is used to identify things can be named as 
appropriate for the data set.  During pipeline creation, Falkonry will identify this 
column and the user will verify the selection.

Example Data
------------

CSV data files are used for source signals (Input data) as well as for verification data. 
Let's look at some examples in detail.

Input data
~~~~~~~~~~

Input data is used to create a pipeline as well as to add source signal data to an 
existing and live pipeline. The input data must contain the following columns: a single 
time column (must be the first column in the data), an optional thing identifier, followed 
by one or more source signals. The header of the CSV file should reflect the appropriate 
column names. 

For example, data used in the Sports Activity example contains the following header::

  time, person, T_xacc, T_yacc, T_zacc, RA_xacc, RA_yacc, RA_zacc, ...

A row of data in that file might look like this::

  1452030355080, p1, 7.9469, 0.29302, 5.604, 1.0998, 0.57985, 6.8342, ...

where ``1452030355080`` is the time value, ``p1`` is the person identifier, and so on.  
The columns after the person column are the raw source data or signal data which Falkonry 
inspects and monitors to provide meaningful condition assessments.

In another example, you can see how UTF-8 characters can be used in the header with a 
different thing identifer::

  time, turbine, LuftTemp Austritt Kühlturm 1, LuftTemp Austritt Kühlturm 2, Drehzahl Lüfter, Temp Auslf WB Scheibe

Verification data
~~~~~~~~~~~~~~~~~

Verification data is used to provide feedback to the Falkonry learning process in order to 
supply condition names as well as to fine tune its findings. The verification data must 
contain a time column (for the interval start), an end column (which must be called "end"), 
an optional thing identifier, followed by one condition label. The header of the CSV file 
should reflect the appropriate column names. For example, data used for verification of 
the Wheel Health data contains the following header::

  time, unit, end, L1 Wheel Health

Note that both the thing identifier and the assessment identified in the header must match 
what has previously been set up in the pipeline.  It is possible to provide more than one 
assessment in the verification data set. Moreover, the values for the assessment are the 
names of condition that are desired to be used in the pipeline. For example, the following 
data from another data set conveys four different episodes being verified::

  time,unit,end,Reliability
  2015-04-22T19:54:02Z,PM-6428,2015-04-22T19:54:04.750Z,Base
  2015-04-22T19:54:05Z,PM-6428,2015-04-22T19:54:06Z,Production
  2015-04-22T19:54:10Z,PM-6428,2015-04-22T19:54:11Z,Production
  2015-04-22T19:54:30Z,PM-6428,2015-04-22T19:54:35Z,Dead Sensor

Output data
~~~~~~~~~~~

Output data can be retrieved from a Falkonry pipeline using its API, or exported manually 
through the Falkonry UI, on the Outflow tab. The main purpose of this output data is to be 
able to view all the assessments and estimates for every thing and timestamp. The output 
data contains one time column, zero or one thing identifier, and one condition assessment.  
For example, the output data of the sports activity example contains the following header::

  time, person, ActivityClassification

Note that both the thing identifier and the assessment identified in the header will match 
what was previously been set up in the pipeline.  If the pipeline produces more than one 
assessment, then each will be present in this data set. Moreover, the values for the 
assessment are the names of conditions that were produced by the pipeline. For example, 
the following data is a snippet of the output from the sports activity pipeline::

  time, person, ActivityClassification
  2016-01-05T21:42:50.000Z, p1, Sitting
  2016-01-05T21:44:48.000Z, p1, Sitting
  2016-01-05T21:45:32.000Z, p1, Walking
  2016-01-05T21:42:24.000Z, p1, Rowing