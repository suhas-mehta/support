Private Deployment
==================

A private deployment of Falkonry can be made into an Infrastructure-as-a-Service provider
such as Microsoft Azure or AWS. It is also possible to provide a private deployment of
Falkonry in your own data center or rack.

System requirements
-------------------

Any deployment of Falkonry should be sized appropriate to the data rate, maximum number
of signals per pipeline, and the number of pipelines. The minimum suggested hardware for
use with Falkonry is the following:

- Hardware 

  - VM and bare metal instances are supported
  - For Falkonry Enterprise

    - Tiny Deployment
      - 1 instance with 4 full cores and 16 GB RAM
      - 100 GB attached free SATA storage
    
    - Medium Deployment
      - 4 instances with 4 full cores and 64 GB RAM each
      - 256 GB attached SATA for root volumes
      - 1 TB SSD for learning buffer volumes
      - 128 GB SSD for internal database volumes

- Software 

  - `Kubernetes v1.1 <http://kubernetes.io/v1.1/gs-custom.html>`_ including 
    `kubectl <http://kubernetes.io/v1.0/docs/user-guide/kubectl/kubectl.html>`_
    The VMs can run any operating systems as long as Kubernetes is fully supported.
  
- Network
 
  - Outbound access to the Internet is required to perform installation.
  - Inbound access for Falkonry DHCS through a jump box

Preparing to Install Falkonry
-----------------------------

Make sure Kubernetes is running and a cluster has been created. Also, ensure that you can
reach the Kubernetes cluster using ``kubectl``. You can confirm this by performing the 
following steps::

  $ kubectl get services
  $ kubectl get rc

Download the Falkonry Installer from `falkonry.com/download <http://falkonry.com/download>`_.

Also, you will need to his step requires the following:
  
- Obtain the following from Falkonry:

  - Software repository credentials for downloading Falkonry Enterprise.
  - Splunk HTTP Event Collector Token for deployment health monitoring.
  - Splunk credentials for application logging.

- Every instance that is part of the Kubernetes cluster will have to login to Falkonry's
  software repository using credentials from the previous step. The command will look like
  the following where the ``-u`` and ``-p`` values will be the credentials provided to you::
  
    docker login -e="." -u="falkonry+installer" -p="9496DSFLGKJ49TS5MGZNW8MK5SDWZDIAKC003ZR8SM71B03UUIVAVOSC66F7S" quay.io
- Decide the configuration for the following properties:

  - Tiny vs. medium size deployment as explained earlier
  - External host name
  - External host protocol. If using `https` ensure that appropriate certificates are set up
    on a proxy server that can forward to port `30061` on the IP address of the Kubernetes 
    master.

Executing the Falkonry Installer
--------------------------------

You can run the Falkonry installer from the downloaded `falkonry.zip` file. To execute the
installer, you will need a shell environment such as `bash` or `tcsh`. Also, make sure
that you run the Falkonry installer from the environment that you can access Kubernetes
from as confirmed in the previous step.

You will run the installer in the following command from the folder where you opened the
Falkonry Installer Zip file::

  $ ./install.sh -c=tiny -h=falkonry.acme.com -p=http -t=splunk-event-collector-token
  
Note that `medium` deployment will require a multi-node Kubernetes cluster and can be 
selected by using the ``-c`` switch above.

The full usage documentation of this installer script is as follows::

  Example : install.sh -c=tiny -h=falkonry.acme.com -p=https -k=kube-secret -t=1234567890 -u=username -s=secret"
    -c | --clusterType   : Cluster type - tiny or medium.
    -h | --host          : Falkonry host to be used. Example - falkonry.acme.com.
    -p | --protocol      : Host protocol to be used - http or https.
    -k | --kubeToken     : Kubernetes authentication token.
    -t | --token         : Splunk token to be used. This is provided by Falkonry.
    -u | --username      : Splunk username to be used. This is provided by Falkonry.
    -s | --password      : Splunk password to be used. This is provided by Falkonry.
