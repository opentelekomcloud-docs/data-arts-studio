:original_name: dataartsstudio_02_0011.html

.. _dataartsstudio_02_0011:

Response
========

After sending a request, you will receive a response, including a status code, response header, and response body.

Status Code
-----------

After sending a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request. For more information, see :ref:`Status Codes <dataartsstudio_02_0310>`.

For example, if status code **201** is returned for calling the API used to obtain a user token, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

If status code **201** is returned for the API used to create an IAM user, the request is successful.

Response Body
-------------

The body of a response is often returned in structured format (for example, JSON or XML) as specified in the **Content-Type** header field. The response body transfers content except the response header.

Part of the response body for the API used to create an IAM user is as follows:

.. code-block::

   {
       "user": {
           "id": "c131886aec...",
           "name": "IAMUser",
           "description": "IAM User Description",
           "areacode": "",
           "phone": "",
           "email": "***@***.com",
           "status": null,
           "enabled": true,
           "pwd_status": false,
           "access_mode": "default",
           "is_domain_owner": false,
           "xuser_id": "",
           "xuser_type": "",
           "password_expires_at": null,
           "create_time": "2024-05-21T09:03:41.000000",
           "domain_id": "d78cbac1..........",
           "xdomain_id": "30086000........",
           "xdomain_type": "",
           "default_project_id": null
       }
   }

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block::

   {
       "error_msg": "Request body is invalid.",
       "error_code": "IAM.0011"
   }

In the response body, **error_code** is an error code, and **error_msg** provides information about the error.
