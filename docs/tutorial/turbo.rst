Turbofan Sensor and Health Prediction 🎥
========================================

Overview
--------

This video demonstrates the use of Falkonry for monitoring the health and function of 
turbofans based on data produced by 
`NASA CMAPSS (Modular Aero-Propulsion System Simulation) <http://www.grc.nasa.gov/WWW/cdtb/software/mapss.html>`_.  
Falkonry evaluates the signal data for seven different sensors on each of 2 turbofan engines.  
The model Falkonry generates is then applied to the signal data from nine additional 
turbofan engines.  The signal data is evaluated and monitored for two conditions: 
*Aerothermal Health*, and *Sensor Health*.  

Concepts covered
----------------

- Overview of Falkonry product and uses
- Falkonry requirements and advantages
- Create pipeline in Falkonry, upload source data
- Create a second Condition for monitoring
- Upload verification data and run a learning cycle
- Make the pipeline "live"
- Add additional data to pipeline from nine additional turbofan engines, previously unknown to Falkonry.
- Overview of Falkonry and Splunk
- Create the Turbofan pipeline in Falkonry from Splunk

Instructions
------------

.. raw:: html

   <iframe src="https://player.vimeo.com/video/150183437" width="500" height="281" frameborder="0" allowfullscreen=""></iframe>

`Turbofan Tutorial <https://vimeo.com/falkonry/turbofan>`_ Video (subscribe to `Falkonry tutorial videos <https://vimeo.com/falkonry>`_ on Vimeo)

Data
----

The tutorial uses 2 data files and 2 verification files below. Click links to download and use:

- Initial data loaded for pipeline creation (can also be found under the library sources
  at the time of pipeline creation):
  `activity_input_part1.csv <https://drive.google.com/uc?export=download&id=0B51xEAJfLP30RENNLWlsOVlRTDQ>`_ 
- Verified examples for Aerothermal Health: `verification.csv <https://drive.google.com/uc?export=download&id=0B51xEAJfLP30NHpuNHMyalI0VzA>`_
- Verified examples for Sensor Health: `sensor_verification.csv <https://drive.google.com/uc?export=download&id=0B51xEAJfLP30NEFSQkVLcXBtaU0>`_
- New data to be used for testing prediction system: `activity_input_part2.csv <https://drive.google.com/uc?export=download&id=0B51xEAJfLP30YVVxbjlYYVhoLVU>`_
- New data to be used for testing prediction system: `turbofan_live_compact.csv <https://drive.google.com/uc?export=download&id=0B51xEAJfLP30ZFZiM1pqc3RCUFU>`_