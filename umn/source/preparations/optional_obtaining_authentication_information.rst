:original_name: dataartsstudio_01_0006.html

.. _dataartsstudio_01_0006:

(Optional) Obtaining Authentication Information
===============================================

When creating OBS links, making API calls, or locating issues, you may need to obtain information such as access keys, project IDs, and endpoints. This section describes how to obtain such information.

Obtaining an Access Key
-----------------------

To obtain an access key, perform the following steps:

#. Log in to the management console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.

#. On the **My Credentials** page, choose **Access Keys**, and click **Create Access Key**. See :ref:`Figure 1 <dataartsstudio_01_0006__en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.

   .. _dataartsstudio_01_0006__en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:

   .. figure:: /_static/images/en-us_image_0000001322088556.png
      :alt: **Figure 1** Clicking Create Access Key

      **Figure 1** Clicking Create Access Key

#. Click **OK** and save the access key file as prompted. The access key file will be saved to your browser's configured download location. Open the **credentials.csv** file to view **Access Key Id** and **Secret Access Key**.

   .. note::

      -  Only two access keys can be added for each user.
      -  To ensure access key security, the access key is automatically downloaded only when it is generated for the first time and cannot be obtained from the management console later. Keep them properly.

.. _dataartsstudio_01_0006__section134096463399:

Obtaining a Project ID and Account ID
-------------------------------------

You can obtain the project ID and account ID by performing the following steps:

#. Register with and log in to the management console.
#. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
#. On the **My Credentials** page, obtain the account name and account ID, and obtain the project ID from the project list.

Obtaining a DataArts Studio Instance ID and Workspace ID
--------------------------------------------------------

To obtain a DataArts Studio instance ID and workspace ID, perform the following steps:

#. On the DataArts Studio console, locate a workspace and click any module, such as **Management Center**.


   .. figure:: /_static/images/en-us_image_0000001322408464.png
      :alt: **Figure 2** Management Center

      **Figure 2** Management Center

#. On the **Management Center** page, obtain the values of **instanceId** and **workspace** in the browser address bar, which are the instance ID and workspace ID, respectively.

   As shown in :ref:`Figure 3 <dataartsstudio_01_0006__en-us_topic_0000001150701582_fig394214118237>`, the instance ID is **6b88…2688**, and the workspace ID is **1dd3bc…d93f0**.

   .. _dataartsstudio_01_0006__en-us_topic_0000001150701582_fig394214118237:

   .. figure:: /_static/images/en-us_image_0000001322408456.png
      :alt: **Figure 3** Obtaining the instance ID and workspace ID

      **Figure 3** Obtaining the instance ID and workspace ID

Obtaining an Endpoint
---------------------

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions.

You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.
