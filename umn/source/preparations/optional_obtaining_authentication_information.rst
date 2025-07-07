:original_name: dataartsstudio_01_0006.html

.. _dataartsstudio_01_0006:

(Optional) Obtaining Authentication Information
===============================================

When using DataArts Studio, for example, when creating OBS links, calling APIs, or locating issues, you may need to obtain information such as access keys, project IDs, and endpoints. This section describes how to obtain such information.

Obtaining an Access Key
-----------------------

To obtain an access key, perform the following steps:

#. Log in to the TICS console, move the cursor to the username in the upper right corner, and select **My Credentials** from the drop-down list.

#. On the **My Credentials** page, choose **Access Keys** > **Create Access Key**. See :ref:`Figure 1 <dataartsstudio_01_0006__en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615>`.

   .. _dataartsstudio_01_0006__en-us_topic_0000001129241845_en-us_topic_0183643042_fig1552229194615:

   .. figure:: /_static/images/en-us_image_0000002270844902.png
      :alt: **Figure 1** Clicking Create Access Key

      **Figure 1** Clicking Create Access Key

#. Click **OK** and save the access key file when prompted. The access key file is saved to the default download location in your browser. Open the **credentials.csv** file to view the access key with an AK and SK.

   .. note::

      -  Only two access keys can be added for each user.
      -  For security purposes, access keys are automatically downloaded only when they are generated for the first time and cannot be obtained from the console later. Keep them properly.

.. _dataartsstudio_01_0006__section134096463399:

Obtaining a Project ID and Account ID
-------------------------------------

A project is a group of tenant resources, and an account ID corresponds to the current account. The IAM ID corresponds to the current user. You can view the project IDs, account IDs, and user IDs in different regions on the corresponding pages.

#. Register with and log in to the management console.
#. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
#. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project ID from the project list.

Obtaining the DataArts Studio Instance ID and Workspace ID
----------------------------------------------------------

You can obtain them from the URI on the DataArts Studio console.

#. On the homepage of the DataArts Studio console, select a workspace, and click a module, for example, **Management Center**.

#. On the **Management Center** page, obtain the values of **instanceId** and **workspace** in the browser address bar, which are the DataArts Studio instance ID and workspace ID, respectively.

   As shown in :ref:`Figure 2 <dataartsstudio_01_0006__en-us_topic_0000001150701582_fig394214118237>`, the instance ID is **6b88…2688**, and the workspace ID is **1dd3bc…d93f0**.

   .. _dataartsstudio_01_0006__en-us_topic_0000001150701582_fig394214118237:

   .. figure:: /_static/images/en-us_image_0000002270956052.png
      :alt: **Figure 2** Obtaining the instance ID and workspace ID

      **Figure 2** Obtaining the instance ID and workspace ID

Obtaining an Endpoint
---------------------

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions.

You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.
