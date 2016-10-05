Falkonry Integration with PI System
===================================

Prerequisites setup of PI System
--------------------------------

While no changes are required to the PI Server, using the pre-built integration of Falkonry
to PI System does require installation and activation of certain PI System components. The 
following steps are required to prepare PI System to be used from Falkonry:

- PI Web API configured to work with the expected AF server.
- Basic authorization method should be configured for PI Web API.
- AF Databases must be crawled and indexed for search in PI system.
- A PI System user account should be created for use with Falkonry.
- Port 443 for secure networking should be accessible on the host where PI Web API is running from the Falkonry Service.

.. note::

Unless these steps are performed, you will not be able to use the Falkonry pre-built integrator. 
Please validate your PI System setup, before performing the following steps to establish the
link between Falkonry and PI System.

Falkonry PI Integration
~~~~~~~~~~~~~~~~~~~~~~~

After logging in to Falkonry Service, click on **Account** in the side drawer and then go to 
**Integration** menu item.


.. image:: ./images/Connect.png


In order to connect to the PI AF server, click on Connect and a panel will appear. The 
following details will need to be provided to setup the connection.

.. note::

The connection between Falkonry Service and PI System is authenticated using Basic Authentication. 
No other authentication methods are currently supported.

.. image:: ./images/ConnectPanel.png

The properties of the PI Web API server required above are:

- Host name
- Port number, ideally 443, where the Web API Server is running
- Context the path where the Web API Server is accessible
- Username used to identify the user 
- Password credentials used to authenticate the user.

.. image:: ./images/ConnectNeededDetails.png

Falkonry Service can connect to the PI AF server once connection to PI Web API server 
is validated. The host to which the connection is established will be visible as the heading 
in the **PI Integrations** section. All links created in this account will use the same 
connection.

.. image:: ./images/Connection.png

In order to start a data flow between Falkonry Service and PI System, you will now create 
a new **Link** to the PI AF server.

Step 1. Select an *Element Template*

Click on the button **Add new Link** and provide the following properties:

  a. *Name*: Choose a name for the event buffer and pipeline created from this *Link*
  b. *Assessment Name*: Provide a name for the assessment produced by the pipeline created from this data
  c. *Data Server*: Choose the Data Server you are going to get data from
  d. *Asset Server*: Next select the Asset Server where the assets are to be retrieved
  e. *Database*: Connect to an AF database of your interest
  f. *Element Template*: Choose an element template that is available in the above chosen database

.. image:: ./images/AddNewLinkPanel.png

Step 2. Select *Element Attributes* to use with Falkonry Service:

As a result of selections made for this *Link*, the attributes related to the selected Asset Template will be brought into Falkonry Service automatically. You can remove/add attributes here by simply crossing them or selecting them from the drop down list.

Step 3. Select elements to use with Falkonry Service:

To bring data of all child entity/elements of the selected element template, select first radio button (Use all Elements based on template) OR if you want to process only selected entity/element then select second radio button (Select Elements From Element Tree) and select the appropriate elements from the tree view.

Step 4. Select time and its configuration:

Choose a time range for the PI System data to populate into Falkonry. Also, you will need to select a timezone to use with your data.

Final Step.

After making all the selections for creating the *Link*, click **Save** and your *Link* will be created.

.. image:: ./images/LinkCreated.png

You can now see the newly created *Event Buffer* and *Pipeline* with name same as the *Link* created in the corresponding list.

.. image:: ./images/EB&PipelineCreated.png

You can navigate to the corresponding PI Wind Turbine **Link** and it takes you to the Event Buffer page where all its details are available.

.. image:: ./images/EBDetails.png

Clicking on the pipeline with the same name in the event buffer details, will take you to the pipeline detail view 

.. image:: ./images/PipelineDetail.png

In the background, Falkonry will continuously pull data from the PI Data Archive and will synchronize with the *Event Buffer* for the corresponding *Link*. All pipelines created from this *Event Buffer* will automatically receive this data. You can verify the availability of the data by clicking on the **Inflow** button on *Pipeline* **Configure Tab**. Once you have the data you can go the **Learn Tab** and create a model for pattern discovery and recognition. 
