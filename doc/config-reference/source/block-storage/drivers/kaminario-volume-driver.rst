==============================================================
Kaminario K2 All-Flash Array iSCSI and FC Cinder drivers
==============================================================

Kaminario's K2 all-flash array leverages a unique software-defined
architecture that delivers predictable performance, scalability and
cost-efficiency-highly valued predictability for the unpredictable
world of the modern datacenter.

Kaminario's K2 all-flash iSCSI and FC arrays can be used in
OpenStack Cinder for providing block-storage using ``KaminarioISCSIDriver``
and ``KaminarioFCDriver`` respectively.

Driver requirements
~~~~~~~~~~~~~~~~~~~

- Following are required:

   -  Kaminario's K2 all-flash iSCSI and/or FC array

   -  K2 rest api version should be >= 2.2.0

   -  krest python library should be installed on block-storage(cinder-volume) node
          - sudo pip install krest

   -  Block-Storage Node should also have data path to K2 array for operations:
          - Create a volume from snapshot
          - Clone a volume, etc

Supported operations
~~~~~~~~~~~~~~~~~~~~

-  Create, delete, attach, and detach volumes.

-  Create and delete volume snapshots.

-  Create a volume from a snapshot.

-  Copy an image to a volume.

-  Copy a volume to an image.

-  Clone a volume.

-  Extend a volume.

-  Retype a volume.

-  Manage and unmanage a volume.

-  Replication with failback support.

Configure Kaminario iSCSI/FC backend
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#. Edit ``/etc/cinder/cinder.conf`` file and define a configuration
   group for iSCSI/FC backend.

   .. code-block:: ini

      [DEFAULT]
      enabled_backends = kaminario

      [kaminario]
      # Management IP of Kaminario K2 All-Flash iSCSI/FC array
      san_ip = 10.0.0.10
      # Management username of Kaminario K2 All-Flash iSCSI/FC array
      san_login = username
      # Management password of Kaminario K2 All-Flash iSCSI/FC array
      san_password = password
      # Enable Kaminario K2 iSCSI/FC driver
      volume_driver = cinder.volume.drivers.kaminario.KaminarioISCSIDriver
      # volume_driver = cinder.volume.drivers.kaminario.KaminarioFCDriver

      # Backend name
      volume_backend_name = kaminario

      # K2 driver calculates max_oversubscription_ratio on setting below
      # option as True. Default value is False
      # auto_calc_max_oversubscription_ratio = False

      # Set a limit on total number of volumes, for example:
      # filter_function = "capabilities.total_volumes < 250"

      # For replication, replication_device must be set
      # Syntax:
      #     replication_device = backend_id:<s-array-ip>,login:<s-username>,password:<s-password>,rpo:<value>
      # where:
      #     s stands for secondary
      #     rpo must be either 60(1 min) or multiple of 300(5 min)
      # Example:
      # replication_device = backend_id:10.0.0.50,login:kaminario,password:kaminario,rpo:300

      # Suppress requests library SSL certificate warnings on setting this option as True
      # Default value is 'False'
      # suppress_requests_ssl_warnings = False

#. Save the changes to the ``/etc/cinder/cinder.conf`` file and
   restart the ``cinder-volume`` service.

Driver options
~~~~~~~~~~~~~~~~~~~~~~

The following table contains the configuration options that are specific
to the Kaminario K2 FC and iSCSI Cinder Drivers

