:original_name: dataartsstudio_01_2515.html

.. _dataartsstudio_01_2515:

Managing Terminal Subscriptions
===============================

Scenario
--------

You can configure terminal subscriptions (SMS messages, emails, and phone calls) by owner. After configuring a subscription, you can use the Manage Notification function to configure a job notification task. When a job runs abnormally or successfully, notifications are sent to the configured owners.

Prerequisites
-------------

Message notification has been enabled and a topic has been configured. Before configuring subscriptions by owner, ensure that you have set a :ref:`job alarm notification topic <dataartsstudio_01_04501__section81976461047>` for the workspace.

Creating a Notification
-----------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Factory**.

#. In the left navigation pane on the DataArts Factory console, choose **Configuration** > **Configure**. Choose **Default Configuration**. For details about how to configure alarm notification topics for workspace jobs by owner, see :ref:`Job Alarm Notification Topic <dataartsstudio_01_04501__section81976461047>`. If you have configured an alarm notification topic, skip this step.


   .. figure:: /_static/images/en-us_image_0000002270791468.png
      :alt: **Figure 1** Setting Job Alarm Notification Topic

      **Figure 1** Setting Job Alarm Notification Topic

#. In the navigation pane on the DataArts Factory page, choose **Monitoring** > **Manage Notification**.

#. Click the **Terminal Subscriptions** tab and click **Add Subscription**. In the displayed dialog box, set required parameters.


   .. figure:: /_static/images/en-us_image_0000002270848338.png
      :alt: **Figure 2** Adding a subscription

      **Figure 2** Adding a subscription

   .. table:: **Table 1** Parameters for adding a subscription

      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Parameter             | Mandatory             | Description                                                           |
      +=======================+=======================+=======================================================================+
      | Owner                 | Yes                   | Set the subscription owner, which was configured during job creation. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Terminal Protocol     | Yes                   | -  SMS                                                                |
      |                       |                       | -  Email                                                              |
      |                       |                       | -  Phone                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+
      | Terminal information  | Yes                   | Set the information about the terminal.                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------+

#. Click **OK**.

#. After the terminal subscription is created, you can perform the following operations on the notification:

   -  Click **Request Subscription**. In the displayed dialog box, the subscription status is **Unconfirmed**. After you click **OK**, the subscription status becomes **Confirmed**.
   -  Click **Delete**. In the **Delete Subscription** dialog box, click **OK** to delete the subscription.

      .. note::

         You can request or delete subscriptions, but cannot edit them.

#. After the preceding operations are complete, configure job alarm notifications by owner on the :ref:`Managing Notifications <dataartsstudio_01_0514>` page.
