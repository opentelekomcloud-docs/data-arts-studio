:original_name: dataartsstudio_02_0317.html

.. _dataartsstudio_02_0317:

Parsing a Stream in a Response Message
======================================

The response messages of the job export API and connection export API are streams that need to be converted to files. For details, see the following sample code:

.. code-block::

   String EXPORT_JOB_URL = "https://{endpoint}/v1/{project_id}/jobs/{job_name}/export";

   try (CloseableHttpClient httpClient = HttpClients.createDefault()) {
       HttpPost httpPost = new HttpPost(EXPORT_JOB_URL);
       httpPost.setHeader("Content-Type", "application/json; charset=UTF-8");
       httpPost.setHeader("Accept", "application/octet-stream");
       httpPost.setHeader("X-Auth-Token", token);

       HttpResponse response = httpClient.execute(httpPost);
       int statusCode = response.getStatusLine().getStatusCode();
       if (statusCode == 200) {
           String filePath = "d:";
           String fileName = "job.zip";
           FileOutputStream fileOutputStream = new FileOutputStream(filePath + fileName);
           response.getEntity().writeTo(fileOutputStream);
       } else {
           System.out.println(statusCode);
       }
   }
