Setup and Integration
=====================

Accessing the Falkonry Service
------------------------------

There are two ways to deploy and use the Falkonry Service depending on your specific 
business needs and requirements.

Service Cloud
~~~~~~~~~~~~~

The simplest way to get immediate and effortless access to the Falkonry service is to take 
advantage of the `Falkonry Service Cloud <https://service.falkonry.io>`_. This allows you to 
focus on creating and refining your pipelines while leaving the infrastructure management 
and maintenance to us. 

When you sign up for the Falkonry Service Cloud, a free Personal account is created for 
you to experiment and learn about the Falkonry Service. You can use your account on the 
Service Cloud to test and evaluate all major functions of the Falkonry Service. If your 
piloting needs exceed the limits of a Personal account (e.g. higher data volumes, greater 
numbers of signals, multiple users), you can purchase a Team account with expanded 
capabilities.

Service Accounts
~~~~~~~~~~~~~~~~

Falkonry provides isolated personal use as well as collaboration workspaces through its
feature called Service Accounts.

.. toctree::
   :maxdepth: 1
   
   accounts

Private Deployment
~~~~~~~~~~~~~~~~~~

The Falkonry Service can be also be deployed into customer-managed virtual private clouds 
on IaaS, or directly onto customer managed compute and storage infrastructure.  There are 
three specific choices then for private deployments:

- VPC deployment on public IaaS cloud providers (Oracle Cloud, MS Azure, or Google Compute 
  Engine): Take advantage of pre-configured deployment environments.
- Virtual Appliance Deployment: Download OVA file and install into standard virtualization 
  environments like Virtual Box
- Install into private Kubernetes environment

.. toctree::
   :maxdepth: 1
   
   appliance
   administration

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
   
   ../connector/rest
   Falkonry Service Python Client Library <http://github.com/falkonry/falkonry-python-client>
   Falkonry Service JavaScript Client Library <http://github.com/falkonry/falkonry-js-client>
   Falkonry Service Java Client Library <http://github.com/falkonry/falkonry-java-client>
   Falkonry Service Csharp Client Library <http://github.com/falkonry/falkonry-csharp-client>

Falkonry Splunk App
-------------------

The Falkonry Splunk App allows existing Splunk customers to connect the Falkonry Service 
directly to Splunk so that the data you are already indexing in Splunk can be easily used
with Falkonry to generate valuable condition assessments. Once you open the outflow
of your Falkonry pipeline, it will continuously produce condition predictions as the data 
flows into Splunk, where you can search and visualize the results using any Splunk tools
directly.

Use the Falkonry Splunk App to work with your existing Splunk data

.. toctree::
   :maxdepth: 1
   
   ../splunk_app/setup.rst
