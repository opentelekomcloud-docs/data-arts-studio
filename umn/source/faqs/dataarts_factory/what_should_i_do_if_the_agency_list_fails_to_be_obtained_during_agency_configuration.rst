:original_name: dataartsstudio_03_0051.html

.. _dataartsstudio_03_0051:

What Should I Do If the Agency List Fails to Be Obtained During Agency Configuration?
=====================================================================================

Possible Causes
---------------

If error message "Policy doesn't allow iam:agencies:listAgencies to be performed." is displayed when you are creating a workspace-level or job-level agency, you may lack the required permissions.

Solution
--------

Add the **View Agency List** policy for the current user.

You can create a custom policy (query the agency list based on specified conditions) and assign it to a user group for refined access control.

#. Log in to the management console.

#. On the management console, hover the mouse pointer over the username in the upper right corner, and choose **Identity and Access Management** from the drop-down list.

#. In the navigation pane, choose **Permissions** > **Roles**. Then, click **Create Custom Policy**.

#. Enter a policy name.


   .. figure:: /_static/images/en-us_image_0000002269195661.png
      :alt: **Figure 1** Policy name

      **Figure 1** Policy name

#. Set **Scope** based on the region where the service is deployed. In this example, you need to grant IAM the permission to query the agency list based on specified conditions. As IAM is a global service, select **Global services** for **Scope**.

#. Select **Visual editor** for **Policy View**.

#. .. _dataartsstudio_03_0051__li1655163417413:

   Configure a policy in **Policy Content**.

   a. Select **Allow**.
   b. Select **Identity and Access Management (IAM)** for **Select service**.
   c. Select **iam:agencies:listAgencies** for **Select action**.

#. Click **OK**.

#. Add the policy defined in :ref:`7 <dataartsstudio_03_0051__li1655163417413>` to the group to which the current user belongs. For details, see "Creating a User Group and Granting Permissions" in the *Identity and Access Management User Guide*.

#. In the navigation pane on the left, choose **Agencies**. Locate the target agency, click **Authorize** in the **Operation** column, add the created custom policy to the agency, and click **OK**.

   The current user can log out of the system and then log in again to obtain the agency list.
