:original_name: dataartsstudio_01_0311.html

.. _dataartsstudio_01_0311:

Configuring a Throttling Policy for API Calling
===============================================

Scenario
--------

A throttling policy limits the maximum number of times that an API can be called within a specific period. Throttling policies can protect the backend service from getting overloaded. Currently, API throttling can limit the number of API calls by user, application, and time period.

To ensure the stability of services, you can create throttling policies to control the calls made to specified APIs. Throttling policies take effect for an API only if they are bound to the API.

.. note::

   An API can be bound to only one throttling policy in an environment, but each throttling policy can be bound to multiple APIs.

Prerequisites
-------------

The API to be bound has been published.

Creating a Throttling Policy
----------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.

3. On the displayed page, choose **Throttling Policies** from the left navigation bar.

4. On the displayed page, click **Create**. Set the parameters listed in :ref:`Table 1 <dataartsstudio_01_0311__en-us_topic_0179716874_table195413315428>`.

   .. _dataartsstudio_01_0311__en-us_topic_0179716874_table195413315428:

   .. table:: **Table 1** Parameters

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                             |
      +===================================+=========================================================================================================================================+
      | Name                              | The throttling policy name.                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Time Range                        | The time duration for limiting the number of API calls                                                                                  |
      |                                   |                                                                                                                                         |
      |                                   | -  Used together with **Max. API Requests** to specify the total number of times an API can be called within a time period.             |
      |                                   | -  Used together with **Max. User Requests** to specify the number of times an API can be called by a user within a time period.        |
      |                                   | -  Used together with **Max. App Requests** to specify the total number of times an API can be called by an app within a time period.   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Max. API Requests                 | The maximum number of times an API can be called within the specified time period.                                                      |
      |                                   |                                                                                                                                         |
      |                                   | Used together with **Time Range** to specify the maximum number of times an API can be called within the period.                        |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Max. User Requests                | The maximum number of times an API can be called by a user within the specified period.                                                 |
      |                                   |                                                                                                                                         |
      |                                   | -  The value of this parameter must be less than that of **Max. API Requests**.                                                         |
      |                                   | -  Used together with **Time Range** to specify the maximum number of times an API can be called by a user within the specified period. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Max. App Requests                 | The maximum number of times an application can be called by a user within the specified period.                                         |
      |                                   |                                                                                                                                         |
      |                                   | -  The value of this parameter must be less than that of **Max. User Requests**.                                                        |
      |                                   | -  Used together with **Time Range** to specify the maximum number of requests an app can make within the specified period.             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | A description of the throttling policy to be created                                                                                    |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

5. Click **OK**.

   After the throttling policy is created, it is listed in the throttling policy list. Bind the throttling policy to an API to limit the access traffic.

Binding a Throttling Policy to an API
-------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.
3. Choose **Throttling Policies** from the left navigation bar.
4. Bind a throttling policy to an API in either of the following ways:

   -  Locate the throttling policy to be bound and click **Associate with APIs**.
   -  Click the target policy name to go to its details page and click **Associate with APIs** on the **List of Associated APIs** tab page.

5. Enter an API group and API name to search for the target API.
6. Select the API and click **OK**.

   .. note::

      If a throttling policy is no longer needed, click **Unbind** on the **List of Associated APIs** tab page. To unbind multiple APIs at a time, select the APIs to be unbound and click **Unbind**. Up to 1000 APIs can be unbound at a time.

Deleting a Throttling Policy
----------------------------

You can delete a throttling policy if it is no longer needed.

#. On the DataArts Studio console, locate a workspace and click **DataArts DataService**.

2. In the left navigation pane, choose an edition, for example, **Exclusive Edition**. The **Overview** page is displayed.
3. On the displayed page, choose **Throttling Policies** from the left navigation bar.
4. On the displayed page, locate the policy you want to unbind and click **Delete** in the **Operation** column.

   .. note::

      -  Throttling policies bound to APIs cannot be deleted. Therefore, you need to unbind them from APIs before deleting them.
      -  To delete multiple throttling policies at a time, select the policies, and click **Delete**. Up to 1000 throttling policies can be deleted at a time.

5. Click **Yes**.
