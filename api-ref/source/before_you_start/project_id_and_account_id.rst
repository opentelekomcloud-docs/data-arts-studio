:original_name: projectid_accountid.html

.. _projectid_accountid:

Project ID and Account ID
=========================

Obtaining a Project ID and Account ID
-------------------------------------

A project is a group of tenant resources, and an account ID corresponds to the current account. The IAM ID corresponds to the current user. You can view the project IDs, account IDs, and user IDs in different regions on the corresponding pages.

#. Register with and log in to the management console.
#. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
#. On the **API Credentials** page, obtain the account name, account ID, IAM username, and IAM user ID, and obtain the project ID from the project list.

Obtaining a Project ID by Calling an API
----------------------------------------

You can obtain the project ID by calling the API to query project information. The API is GET https://{Endpoint}/v3/projects, in which {Endpoint} is the IAM endpoint and can be obtained from IAM documentation.

For details about API authentication, see :ref:`Authentication <dataartsstudio_02_0010>`.

The following is a response example. The value of **id** under **projects** is the project ID. If multiple IDs are returned, obtain the desired one based on your actual region (name).

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "region-name",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }
