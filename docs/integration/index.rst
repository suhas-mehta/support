Integration
===========

REST API
--------

This document will focus on using the Falkonry REST API and will explore two different 
ways to access it: 

  - Falkonry Service API page - This is an interactive web page which allows you to easily 
    examine and test the various UI functions.
  - Programmatic API use - Use of the API programmatically from your application. 

When using the API programmatically, e.g., from the command line or from a Java 
application, you will need to use an API token obtained from the Falkonry Service UI. 

You can generate an API Token from the **Account** Settings for **Integration**. This screen
allows you to generate as many different tokens as you wish. The name of the token
is used to identify the user that performs API actions.

.. image:: ./api/images/auth-token.png

This token will be used in HTTP requests that are sent to Falkonry in the rest of this 
document. 

.. toctree::
   :maxdepth: 3
   
   api/live
   api/buffer/index
   api/pipeline/index

Prebuilt Connectors
-------------------

MQTT and AMQP Brokers
~~~~~~~~~~~~~~~~~~~~~

`MQTT <http://mqtt.org/>`_ is a widely-used, machine-to-machine (M2M)/"Internet of Things" connectivity protocol. The `Advanced Message Queuing Protocol (AMQP) <https://www.amqp.org/>`_ is an open standard for passing business messages between applications or organizations.

The Falkonry Service natively supports use of MQTT and AMQP brokers for inbound and outbound data communication. Configuration is straightforward - for inbound communication Event Buffers subscribe to a broker topic, and for outbound communication Pipelines can publish output to a broker topic.  See the following sections in the User Guide:

  - `Event Buffer Subscriptions <../using/eventbuffer.html#event-buffer-subscription-to-mqtt-broker>`_
  - `Publishing Pipeline Output <../using/configure.html#through-a-client-application>`_

Falkonry Splunk App
~~~~~~~~~~~~~~~~~~~

The Falkonry Splunk App allows existing `Splunk <http://www.splunk.com/>`_ customers to connect the Falkonry Service directly to Splunk so that the data in Splunk can be easily used with Falkonry to generate valuable condition assessments. The Splunk App (accessed within the Splunk application environment) will configure flow from Splunk to a Falkonry Event Buffer, and flow of condition assessment results back into Splunk.  The Falkonry Splunk App is available as a free download.

.. toctree::
   :maxdepth: 1
   
   ../splunk_app/setup.rst

Falkonry PI Integrator
~~~~~~~~~~~~~~~~~~~~~~

The `OSISoft PI System <http://www.osisoft.com/pi-system/>`_ is a suite of software products that are used for data collection, historicizing, finding, analyzing, delivering, and visualizing. It is marketed as an enterprise infrastructure for management of real-time data and events.  Falkonry provides a pre-built integrator for the PI System.  

.. toctree::
   :maxdepth: 1
   
   ./pi/example
   ./pi/index
   
Build Your Own Connectors
-------------------------

Who is it for?
~~~~~~~~~~~~~~

If you want to integrate your application directly with Falkonry, then you can use the 
Falkonry API or client libraries. 

.. note::

  Please remember that Falkonry API is a Beta Preview. Things are subject to change, and 
  there might be a few rough edges.

Before you can use the Falkonry API you must have a Falkonry account.  Create an account 
from the `Falkonry Website <http://falkonry.com/start>`_.  Additionally, this document 
assumes knowledge of `Falkonry AI concepts <../concepts.html>`_ and the Falkonry UI.  
   
Connector Technologies
~~~~~~~~~~~~~~~~~~~~~~

There are several ways to interact with the Falkonry service.  Whether you are 
creating a pipeline or uploading source data, you currently have a number of choices besides
the `Falkonry UI <../concepts.html>`_ and `Falkonry Splunk App <../splunk_app/index.html>`_:
      
.. toctree::
   :maxdepth: 3
   
   Falkonry Service Python Client Library <http://github.com/falkonry/falkonry-python-client>
   Falkonry Service JavaScript Client Library <http://github.com/falkonry/falkonry-js-client>
   Falkonry Service Java Client Library <http://github.com/falkonry/falkonry-java-client>
   Falkonry Service Csharp Client Library <http://github.com/falkonry/falkonry-csharp-client>
