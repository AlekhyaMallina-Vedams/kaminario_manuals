..
    Warning: Do not edit this file. It is automatically generated from the
    software project's code and your changes will be overwritten.

    The tool to generate this file lives in openstack-doc-tools repository.

    Please make any changes needed in the code, then run the
    autogenerate-config-doc tool from the openstack-doc-tools repository, or
    ask for help on the documentation mailing list, IRC channel or meeting.

.. _aodh-common:

.. list-table:: Description of common configuration options
   :header-rows: 1
   :class: config-ref-table

   * - Configuration option = Default value
     - Description
   * - **[DEFAULT]**
     -
   * - ``evaluation_interval`` = ``60``
     - (Integer) Period of evaluation cycle, should be >= than configured pipeline interval for collection of underlying meters.
   * - ``event_alarm_cache_ttl`` = ``60``
     - (Integer) TTL of event alarm caches, in seconds. Set to 0 to disable caching.
   * - ``executor_thread_pool_size`` = ``64``
     - (Integer) Size of executor thread pool.
   * - ``http_timeout`` = ``600``
     - (Integer) Timeout seconds for HTTP requests. Set it to None to disable timeout.
   * - ``notifier_topic`` = ``alarming``
     - (String) The topic that aodh uses for alarm notifier messages.
   * - ``record_history`` = ``True``
     - (Boolean) Record alarm change events.
   * - ``rest_notifier_certificate_file`` =
     - (String) SSL Client certificate file for REST notifier.
   * - ``rest_notifier_certificate_key`` =
     - (String) SSL Client private key file for REST notifier.
   * - ``rest_notifier_max_retries`` = ``0``
     - (Integer) Number of retries for REST notifier
   * - ``rest_notifier_ssl_verify`` = ``True``
     - (Boolean) Whether to verify the SSL Server certificate when calling alarm action.
   * - **[database]**
     -
   * - ``alarm_history_time_to_live`` = ``-1``
     - (Integer) Number of seconds that alarm histories are kept in the database for (<= 0 means forever).
   * - **[service_credentials]**
     -
   * - ``interface`` = ``public``
     - (String) Type of endpoint in Identity service catalog to use for communication with OpenStack services.
   * - ``region_name`` = ``None``
     - (String) Region name to use for OpenStack service endpoints.
