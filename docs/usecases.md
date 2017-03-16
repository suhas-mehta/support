Examples and Use Cases
================

The Falkonry Service can be used to support a wide variety of condition prediction 
problems, and can flexibly be embedded in different modes of use.

The most common use of the Falkonry Service is to determine the condition of physical 
systems (e.g. stationary industrial equipment, vehicles, appliances, devices) from 
multivariate, time-series data produced from those systems.  A real-time understanding the 
condition of theses systems can be used for many purposes

- Health and safety monitoring
- Preventive maintenance scheduling
- Performance optimization
- Service and insurance pricing
- Malicious behavior monitoring

There are two primary modes of use of the Falkonry Service

- Extending operational analysis capabilities:  here the Falkonry Service is used in conjunction with time-series analysis product like Splunk or an industrial data historian
- Embedding condition prediction in IoT applications: here the Falkonry Service is embedded in a packaged or custom IoT application

Extending operational analytics
-------------------------------

With the Falkonry Service a Splunk user add powerful condition prediction capabilities to 
the time-series analysis capabilities they already have in Splunk.  The Falkonry Splunk 
App makes it easy for a Splunk user to pipe machine data to the Falkonry Service and get 
back a set of condition predictions ready for use in the Splunk environment.

Any repository of time-series data can be used in a similar manner with the Falkonry 
Service to add streaming condition prediction to existing time-series search and analysis 
capabilities.

Embedding condition prediction in IoT applications
--------------------------------------------------

New IoT applications are being built and deployed at an ever increasing rate, and there is
a growing ecosystem of platforms, tools, and infrastructure to support these applications 
(e.g. application development platforms like SeeControl and ThingWorx, connectivity 
platforms, data platforms, sensor frameworks, deployment infrastructure, etc.).  

The Falkonry Service provides an easily embeddable means of adding condition prediction to 
any IoT application.  

Tutorial videos
---------------

.. toctree::
   :maxdepth: 2

   tutorial/index