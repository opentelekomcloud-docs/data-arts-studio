:original_name: dataartsstudio_02_0314.html

.. _dataartsstudio_02_0314:

Project ID and Account ID
=========================

Obtaining a Project ID and Account ID
-------------------------------------

You can obtain the project ID and account ID by performing the following steps:

#. Register with and log in to the management console.
#. Hover the cursor on the username in the upper right corner and select **My Credentials** from the drop-down list.
#. On the **My Credentials** page, obtain the account name and account ID, and obtain the project ID from the project list.

Obtaining a Project ID by Calling an API
----------------------------------------

You can obtain a project ID by calling the API used to query projects based on specified criteria.

The API for obtaining a project ID is **GET https://**\ *{Endpoint}*\ **/v3/projects/**, where *{Endpoint}* indicates the endpoint of IAM.

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

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
