:original_name: apiOverview_DLS.html

.. _apiOverview_DLS:

DataArts Security API Overview
==============================

.. table:: **Table 1** DataArts Security API types

   +--------------------------------------------------------------------------------+----------------------------+
   | Type                                                                           | Description                |
   +================================================================================+============================+
   | :ref:`Permission Management <apioverview_dls__section_tag_child_866107488563>` | Permission management APIs |
   +--------------------------------------------------------------------------------+----------------------------+
   | :ref:`Identification Rule <apioverview_dls__section_tag_child_068564548708>`   | Identification rule APIs   |
   +--------------------------------------------------------------------------------+----------------------------+
   | :ref:`Rule Group <apioverview_dls__section_tag_child_046730457067>`            | Rule group APIs            |
   +--------------------------------------------------------------------------------+----------------------------+

.. _apioverview_dls__section_tag_child_866107488563:

Permission Management
---------------------

.. table:: **Table 2** Permission management

   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | API                                                                                             | Description                                                     |
   +=================================================================================================+=================================================================+
   | :ref:`Creating a Permission Set <createsecuritypermissionset>`                                  | This API is used to create a permission set.                    |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Querying the Permission Set List <listsecuritypermissionsets>`                            | This API is used to query the permission set list.              |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Querying a Permission Set <showsecuritypermissionset>`                                    | This API is used to query a permission set.                     |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Deleting a Permission Set <deletesecuritypermissionset>`                                  | This API is used to delete a permission set.                    |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Updating a Permission Set <updatesecuritypermissionset>`                                  | This API is used to update a permission set.                    |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Adding a Member to a Permission Set <createsecuritypermissionsetmember>`                  | This API is used to add a member to a permission set.           |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Querying Members of a Permission Set <listsecuritypermissionsetmembers>`                  | This API is used to query the members of a permission set.      |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Deleting Members of a Permission Set <batchdeletesecuritypermissionsetmembers>`           | This API is used to delete members of a permission set.         |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Adding Permissions to a Permission Set <createsecuritypermissionsetpermission>`           | This API is used to add permissions to a permission set.        |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Querying Permissions in a Permission Set <listsecuritypermissionsetpermissions>`          | This API is used to query the permissions in a permission set.  |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Deleting Permissions from a Permission Set <batchdeletesecuritypermissionsetpermissions>` | This API is used to delete permissions from a permission set.   |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
   | :ref:`Updating Permissions in a Permission Set <updatesecuritypermissionsetpermission>`         | This API is used to update the permissions in a permission set. |
   +-------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+

.. _apioverview_dls__section_tag_child_068564548708:

Identification Rule
-------------------

.. table:: **Table 3** Identification Rule

   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | API                                                                                  | Description                                                |
   +======================================================================================+============================================================+
   | :ref:`Querying the Identification Rule List <listsecuritydataclassificationrules>`   | This API is used to query the identification rule list.    |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Creating an Identification Rule <createsecuritydataclassificationrule>`        | This API is used to create an identification rule.         |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Querying a Specified Identification Rule <showsecuritydataclassificationrule>` | This API is used to query a specified identification rule. |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Deleting an Identification Rule <deletesecuritydataclassificationrule>`        | This API is used to delete an identification rule.         |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Modifying an Identification Rule <updatesecuritydataclassificationrule>`       | This API is used to modify an identification rule.         |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Deleting Identification Rules <batchdeletesecuritydataclassificationrule>`     | This API is used to delete identification rules.           |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+
   | :ref:`Modifying the Identification Rule Status <updatesecurityruleenablestatus>`     | This API is used to modify the identification rule status. |
   +--------------------------------------------------------------------------------------+------------------------------------------------------------+

.. _apioverview_dls__section_tag_child_046730457067:

Rule Group
----------

.. table:: **Table 4** Rule group

   +--------------------------------------------------------------------------------+------------------------------------------------+
   | API                                                                            | Description                                    |
   +================================================================================+================================================+
   | :ref:`Querying the Rule Group List <listsecuritydataclassificationrulegroups>` | This API is used to query the rule group list. |
   +--------------------------------------------------------------------------------+------------------------------------------------+
   | :ref:`Querying a Rule Group <showsecuritydataclassificationrulegroup>`         | This API is used to query a rule group.        |
   +--------------------------------------------------------------------------------+------------------------------------------------+
