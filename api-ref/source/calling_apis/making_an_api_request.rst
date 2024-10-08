:original_name: making_request.html

.. _making_request:

Making an API Request
=====================

This section describes the structure of a REST API, and uses the IAM API for obtaining a user token as an example to demonstrate how to call an API. The obtained token can then be used to authenticate the calling of other APIs.

Request URI
-----------

A request URI is in the following format:

**{URI-scheme}://{Endpoint}/{resource-path}?{query-string}**

Although a request URI is included in the request header, most programming languages or frameworks require the request URI to be transmitted separately.

.. table:: **Table 1** URI parameters

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                          |
   +===================================+======================================================================================================================================================================================================================================================================+
   | URI-scheme                        | Protocol used to transmit requests. All APIs use HTTPS.                                                                                                                                                                                                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint                          | Domain name or IP address of the server bearing the REST service endpoint. The endpoint varies between services in different regions.                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                      |
   |                                   | An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. You can obtain endpoints of the service from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                      |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path                     | Access path of an API for performing a specified operation. Obtain the value from the URI of an API. For example, the **resource-path** of the API used to obtain a user token is **/v3/auth/tokens**.                                                               |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string                      | Query parameter, which is optional. Ensure that a question mark (**?**) is included before each query parameter that is in the format of "*Parameter name=Parameter value*", for example, **?limit=10**, it indicates that a maximum of 10 data records are allowed. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   To simplify the URI display in this document, each API is provided only with a **resource-path** and a request method. The **URI-scheme** value of all APIs is **HTTPS**, and the endpoints of all APIs in the same region are identical.

Request Method
--------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

.. table:: **Table 2** HTTP methods

   +-----------------------------------+----------------------------------------------------------------------------+
   | Method                            | Description                                                                |
   +===================================+============================================================================+
   | GET                               | Requests the server to return specified resources.                         |
   +-----------------------------------+----------------------------------------------------------------------------+
   | PUT                               | Requests the server to update specified resources.                         |
   +-----------------------------------+----------------------------------------------------------------------------+
   | POST                              | Requests the server to add resources or perform special operations.        |
   +-----------------------------------+----------------------------------------------------------------------------+
   | DELETE                            | Requests the server to delete specified resources, for example, an object. |
   +-----------------------------------+----------------------------------------------------------------------------+
   | HEAD                              | Same as GET except that the server must return only the response header.   |
   +-----------------------------------+----------------------------------------------------------------------------+
   | PATCH                             | Requests the server to update partial content of a specified resource.     |
   |                                   |                                                                            |
   |                                   | If the resource does not exist, a new resource will be created.            |
   +-----------------------------------+----------------------------------------------------------------------------+

For example, in the URI of the IAM API used to obtain a user token, the request method is POST. The request is as follows:

.. code-block:: text

   POST https://{{IAM endpoint}}/v3/auth/tokens

Request Header
--------------

You can also add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, to request the authentication information, add **Content-Type**, which specifies the request body type.

:ref:`Table 3 <making_request__en-us_topic_0181281315_en-us_topic_0170647348_en-us_topic_0121682347_table1986821153312>` lists common request header fields.

.. _making_request__en-us_topic_0181281315_en-us_topic_0170647348_en-us_topic_0121682347_table1986821153312:

.. table:: **Table 3** Common request header fields

   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Field           | Description                                                                                                                                                                                                                                                                                             | Mandatory                                                                                                                                                                                                                                    | Example                                    |
   +=================+=========================================================================================================================================================================================================================================================================================================+==============================================================================================================================================================================================================================================+============================================+
   | Content-Type    | Request body type or format. Its default value is **application/json**.                                                                                                                                                                                                                                 | Yes                                                                                                                                                                                                                                          | application/json                           |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Content-Length  | Specifies the length of the request body. The unit is byte.                                                                                                                                                                                                                                             | No                                                                                                                                                                                                                                           | 3495                                       |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Language      | Specifies the request language.                                                                                                                                                                                                                                                                         | No                                                                                                                                                                                                                                           | en_us                                      |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Project-Id    | Specifies a project ID. Obtain the project ID by following the instructions in :ref:`Project ID and Account ID <projectid_accountid>`.                                                                                                                                                                  | No                                                                                                                                                                                                                                           | e9993fc787d94b6c886cbaa340f9c0f4           |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Auth-Token    | Specifies a user token.                                                                                                                                                                                                                                                                                 | This field is mandatory for token authentication.                                                                                                                                                                                            | The following is part of an example token: |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 | The user token is a response to the API used to obtain a user token. This API is the only one that does not require authentication.                                                                                                                                                                     |                                                                                                                                                                                                                                              | MIIPAgYJKoZIhvcNAQcCo...ggg1BBIINPXsidG9rZ |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 | The token is the value of **X-Subject-Token** in the response header.                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                              |                                            |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Sdk-Date      | Time when the request is sent. The time is in **YYYYMMDD'T'HHMMSS'Z'** format.                                                                                                                                                                                                                          | This field is mandatory for AK/SK-based authentication.                                                                                                                                                                                      | 20150907T101459Z                           |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 | The value is the current GMT time of the system.                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                              |                                            |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Host            | Specifies the server domain name and port number of the resources being requested. The value can be obtained from the URL of the service API. The value is in the format of *hostname[:port]*. If the port number is not specified, the default port is used. The default port number for HTTPS is 443. | This field is mandatory for AK/SK-based authentication.                                                                                                                                                                                      | code.test.com                              |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              | or                                         |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              | code.test.com:443                          |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Authorization   | Authentication information.                                                                                                                                                                                                                                                                             | This field is mandatory for AK/SK-based authentication.                                                                                                                                                                                      | ``-``                                      |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 | The value can be obtained from the request signing result.                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                              |                                            |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | workspace       | Workspace ID. For details about how to obtain it, see :ref:`DataArts Studio Instance ID and Workspace ID <dataartsstudio_02_0350>`.                                                                                                                                                                     | -  You do not need to set this field when calling a CDM API because in that case, only the default workspace can be used.                                                                                                                    | d1cd7861478748a6925bc02f47c69279           |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 |                                                                                                                                                                                                                                                                                                         | -  This field is mandatory when there are multiple DataArts Studio instances during a call to a data development API.                                                                                                                        |                                            |
   |                 |                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                              |                                            |
   |                 |                                                                                                                                                                                                                                                                                                         |    This field is optional when there is only one DataArts Studio instance. If this field is not specified, data in the default workspace is queried by default. To query data in other workspaces, include this field in the request header. |                                            |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Dlm-Type      | DataArts DataService edition, which is Exclusive                                                                                                                                                                                                                                                        | This parameter is mandatory for calling DataArts DataService APIs.                                                                                                                                                                           | **EXCLUSIVE**: exclusive edition           |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+

.. note::

   In addition to supporting token-based authentication, APIs also support authentication using access key ID/secret access key (AK/SK). During AK/SK-based authentication, an SDK is used to sign the request, and the **Authorization** (signature authentication) and **X-Sdk-Date** (time when the request is sent) header fields are automatically added to the request.

   For more information, see "AK/SK-based Authentication" in :ref:`Authentication <dataartsstudio_02_0010>`.

The API used to obtain a user token does not require authentication. Therefore, only the **Content-Type** field needs to be added to requests for calling the API. An example of such requests is as follows:

.. code-block:: text

   POST https://{{endpoint}}/v3/auth/tokens
   Content-Type: application/json

Request Body
------------

The body of a request is often sent in a structured format as specified in the **Content-Type** header field. The request body transfers content except the request header.

The request body varies between APIs. Some APIs do not require the request body, such as the APIs requested using the **GET** and **DELETE** methods.

In the case of the API used to obtain a user token, the request parameters and parameter description can be obtained from the API request. The following provides an example request with a body included. Replace *username*, *domainname*, ``********`` (login password), and *xxxxxxxxxxxxxxxxxx* (project ID) with the actual values. To learn how to obtain a project ID, see :ref:`Project ID and Account ID <projectid_accountid>`.

.. note::

   The **scope** parameter specifies where a token takes effect. You can set **scope** to an account or a project under an account..

.. code-block::

   POST https://{{endpoint}}/v3/auth/tokens
   Content-Type: application/json

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "id": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }

If all data required for the API request is available, you can send the request to call the API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding. For the API used to obtain a user token, **x-subject-token** in the response header is the desired user token. This token can then be used to authenticate the calling of other APIs.
