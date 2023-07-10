:original_name: dataartsstudio_03_0051.html

.. _dataartsstudio_03_0051:

What Should I Do If the Agency List Fails to Be Obtained During Agency Configuration?
=====================================================================================

When a workspace- or job-level agency is configured, the following error is reported when the agency list is viewed:

Policy doesn't allow iam:agencies:listAgencies to be performed.

Add the **View Agency List** policy for the current user.

You can create a custom policy (query the agency list based on specified conditions) and assign it to a user group for refined access control.

#. Log in to the management console.

#. On the management console, hover the mouse pointer over the username in the upper right corner, and choose **Identity and Access Management** from the drop-down list.

#. In the navigation pane, choose **Permissions**. Then, click **Create Custom Policy**.

#. Enter a policy name.

   |image1|

#. Set **Scope** to **Global services**. The scope you set is where the custom policy takes effect. In this example, the custom policy has the permissions required to view the agency lists based on specified conditions.

#. Set **Policy View** to **Visual editor**.

#. .. _dataartsstudio_03_0051__li11144122232119:

   Configure a policy in **Policy Content**.

   a. Select **Allow**.
   b. Select **Identity and Access Management (IAM)** for **Select service**.
   c. Select **iam:agencies:listAgencies** for **Select action**.

#. Click **OK**.

#. Add the policy defined in :ref:`7 <dataartsstudio_03_0051__li11144122232119>` to the group to which the current user belongs. For details, see "Creating a User Group and Granting Permissions" in the *Identity and Access Management User Guide*.

   The current user can log out of the system and then log in again to obtain the agency list.

.. |image1| image:: /_static/images/en-us_image_0000001373409249.png
