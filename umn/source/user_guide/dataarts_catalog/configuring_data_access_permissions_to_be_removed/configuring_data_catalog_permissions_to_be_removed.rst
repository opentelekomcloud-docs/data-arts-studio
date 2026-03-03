:original_name: dataartsstudio_01_0818.html

.. _dataartsstudio_01_0818:

Configuring Data Catalog Permissions (To Be Removed)
====================================================

You can manage data catalog permissions.

.. important::

   Data permission capabilities are provided by DataArts Security, and no longer by DataArts Catalog in regions where DataArts Security is available. The data permission functions in DataArts Catalog are available only to existing users.

Constraints
-----------

-  Only workspace admins can create, delete, and modify data catalog permissions rules and set the permissions effective status.
-  Workspace developers, operators, and viewers can only view data permissions.

Managing a Data Catalog Permissions Rule
----------------------------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Catalog**.

2. Choose **Permissions** > **Data Catalog Permissions** from the left navigation bar, and click **Create** on the page displayed to configure a data catalog permissions rule.

   a. **Rule**: Name of a data catalog permissions rule.
   b. **Type**: Currently, only **Tag**, **Security level**, and **Classification** can be used for filtering.
   c. **Scope**: Select available tags, security levels, and classifications.
   d. **User**: User to whom the configured data catalog permissions rule applies.
   e. **Validate**: If this function is enabled, the data catalog permissions rule takes effect. Otherwise, the rule does not take effect.

   .. note::

      After a data catalog permissions rule takes effect, only users to whom the configured data directory permissions rule applies can manage data assets with specified tags or classifications. For example, if **Type** is set to **Tag**, **Scope** is set to **test**, and **User** is set to **A**, user A can manage assets with tag **test** after the permissions rule is enabled.


   .. figure:: /_static/images/en-us_image_0000002269123285.png
      :alt: **Figure 1** Creating a rule

      **Figure 1** Creating a rule

3. In the data catalog permissions rule list, click **Edit** or **Delete** in the **Operation** column to modify or delete the rule.
