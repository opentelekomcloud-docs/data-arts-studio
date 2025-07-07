:original_name: dataartsstudio_01_5105.html

.. _dataartsstudio_01_5105:

Configuring Environment Isolation for a Workspace in Enterprise Mode
====================================================================

-  You can configure isolation between the development and production environments for DLI and DB.
-  After the environment isolation is configured, the data connection in the development environment in the script or job during data development is automatically switched to the data connection in the production environment after the process is released.

Prerequisites
-------------

-  Before configuring environment isolation for DLI, ensure that you have created a DLI :ref:`data connection <dataartsstudio_01_1299>`.

(Optional) Configuring DLI Environment Isolation
------------------------------------------------

Environment isolation needs to be configured only for a serverless service (that is, DLI).

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. In the left navigation pane on the **Management Center** page, choose **Data Source Resource Mapping Configuration**.


   .. figure:: /_static/images/en-us_image_0000002270847226.png
      :alt: **Figure 1** Data Source Resource Mapping Configuration

      **Figure 1** Data Source Resource Mapping Configuration

#. Click the **DB Configuration** tab and then **Add**. Set the database names for the development and production environments respectively and click **Save**. You can click |image1| and |image2| to edit and delete records.

   The database names must be the names of created databases. It is recommended that the database name for the development environment be the same as that for the production environment, and that suffix **\_dev** be added to the database name for the development environment so that it can be distinguished from the database name for the production environment.


   .. figure:: /_static/images/en-us_image_0000002305833085.png
      :alt: **Figure 2** DB Configuration

      **Figure 2** DB Configuration

#. Click the **DLI Queue Configuration** tab and then **Add**. Set the queue names for the development and production environments respectively and click **Save**. You can use |image3| and |image4| to edit and delete records.

   The queue names must be the names of created DLI queues. It is recommended that the queue name for the development environment be the same as that for the production environment, and that suffix **\_dev** be added to the queue name for the development environment so that it can be distinguished from the queue name for the production environment.


   .. figure:: /_static/images/en-us_image_0000002270847214.png
      :alt: **Figure 3** DLI Queue Configuration

      **Figure 3** DLI Queue Configuration

#. After the preceding operations are complete, DLI environment isolation configuration is complete.

.. _dataartsstudio_01_5105__section20609134272018:

DB Configuration
----------------

#. On the DataArts Studio console, locate a workspace and click **Management Center**.

#. In the left navigation pane on the **Management Center** page, choose **Data Source Resource Mapping Configuration**.

#. Click the **DB Configuration** tab and then **Add**. Set the database names for the development and production environments respectively and click **Save**. You can click |image5| and |image6| to edit and delete records.

   The database names must be the names of created databases. It is recommended that the database name for the development environment be the same as that for the production environment, and that suffix **\_dev** be added to the database name for the development environment so that it can be distinguished from the database name for the production environment.

   .. important::

      For GaussDB(DWS), MRS Hive, and MRS Spark, if you **select the same cluster** when creating a data connection, you must configure database mapping on the **Configure Data Source Resource Mapping** page to isolate the development and production environments.


   .. figure:: /_static/images/en-us_image_0000002271193404.png
      :alt: **Figure 4** DB Configuration

      **Figure 4** DB Configuration

.. |image1| image:: /_static/images/en-us_image_0000002305440189.png
.. |image2| image:: /_static/images/en-us_image_0000002305440173.png
.. |image3| image:: /_static/images/en-us_image_0000002305440181.png
.. |image4| image:: /_static/images/en-us_image_0000002305407129.png
.. |image5| image:: /_static/images/en-us_image_0000002305440161.png
.. |image6| image:: /_static/images/en-us_image_0000002305407121.png
