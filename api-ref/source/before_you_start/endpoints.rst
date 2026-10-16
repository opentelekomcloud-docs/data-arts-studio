:original_name: dataartsstudio_02_0004.html

.. _dataartsstudio_02_0004:

Endpoints
=========

Obtaining an Endpoint
---------------------

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions.

The endpoint of each service consists of the service name, region ID, and domain name. The format is as follows: *service_name.region_id.domain_name*. Select the endpoint of the required region. The service names of DataArts Studio modules are different:

-  DataArts Migration API: cdm.\ **{region_id}**.\ **{domain_name}**
-  DataArts Factory API: dayu-dlf.\ **{region_id}**.\ **{domain_name}**
-  APIs of other DataArts Studio modules (such as Management Center, DataArts Architecture, DataArts Quality, DataArts Catalog, DataArts DataService, DataArts Security, and Data Maps): dayu.\ **{region_id}**.\ **{domain_name}**

You can obtain endpoints from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.
