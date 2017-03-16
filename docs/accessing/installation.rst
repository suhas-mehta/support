Installation
=================

The Falkonry Service can be installed on any bare metal or virtualized hardware that
supports `Docker 1.12 <http://docker.com>`_. The goal of the Falkonry Server 
Deployment is to provide a quick installation process that is completely under your
control and disconnected from the network.

.. note::

 To obtain the Falkonry Service Software, please contact us at `sales@falkonry.com`.

System requirements
-------------------

Any deployment of Falkonry should be sized appropriate to the data rate, maximum number
of signals per pipeline, and the number of pipelines. The minimum suggested hardware for
use with Falkonry is the following:

- Hardware 

  - A minimum of

   - 4 full cores and 16 GB RAM
   - 128 GB attached SATA for root volumes
   - 256 GB SSD for internal database volumes

- Software 

  - Docker 1.12

Installation Steps
----------------------------

Once you've downloaded your Falkonry tarball file you can run the script `Falkonry-Docker.sh`
from the folder where you have opened the tarball

After the installation script completes, Falkonry Service is accessible via a web browser at http://localhost:8080.

Please read about `Service Administration <./administration.html>`_ before continuing to the next step.
You will need to install a license first.

.. note::
  You can log in using any email address and name. The information you enter here is used solely
  for identifying your account. 
