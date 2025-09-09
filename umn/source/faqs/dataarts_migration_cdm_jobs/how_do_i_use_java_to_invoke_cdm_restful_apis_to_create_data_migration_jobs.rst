:original_name: dataartsstudio_03_0101.html

.. _dataartsstudio_03_0101:

How Do I Use Java to Invoke CDM RESTful APIs to Create Data Migration Jobs?
===========================================================================

CDM provides RESTful APIs to implement automatic job creation or execution control by program invocation.

The following describes how to use CDM to migrate data from table **city1** in the MySQL database to table **city2** on DWS, and how to use Java to invoke CDM RESTful APIs to create, start, query, and delete a CDM job.

Prepare the following data in advance:

#. Username, account name, and project ID of the cloud account

#. Create a CDM cluster and obtain the cluster ID.

   On the **Cluster Management** page, click the CDM cluster name to view the cluster ID, for example, **c110beff-0f11-4e75-8b10-da7cd882b0ef**.

#. Create a MySQL database and a DWS database, and create tables **city1** and **city2**. The statements for creating tables are as follows:

   .. code-block::

      MySQL:
      create table city1(code varchar(10),name varchar(32));
      insert into city1 values('NY','New York');
      DWS:
      create table city2(code varchar(10),name varchar(32));

#. In the CDM cluster, create a link to MySQL, such as a link named **mysqltestlink**. Create a link to DWS, such as a link named **dwstestlink**.

#. Run the following code. You are advised to use the HttpClient package of version 4.5. Maven configuration is as follows:

   .. code-block::

      <project>
      <modelVersion>4.0.0</modelVersion>
      <groupId>cdm</groupId>
      <artifactId>cdm-client</artifactId>
      <version>1</version>
      <dependencies>
      <dependency>
      <groupId>org.apache.httpcomponents</groupId>
      <artifactId>httpclient</artifactId>
      <version>4.5</version>
      </dependency>
      </dependencies>
      </project>

Sample Code
-----------

The code for using Java to invoke CDM RESTful APIs to create, start, query, and delete a CDM job is as follows:

.. code-block::

   package cdmclient;
   import java.io.IOException;
   import org.apache.http.Header;
   import org.apache.http.HttpEntity;
   import org.apache.http.HttpHost;
   import org.apache.http.auth.AuthScope;
   import org.apache.http.auth.UsernamePasswordCredentials;
   import org.apache.http.client.CredentialsProvider;
   import org.apache.http.client.config.RequestConfig;
   import org.apache.http.client.methods.CloseableHttpResponse;
   import org.apache.http.client.methods.HttpDelete;
   import org.apache.http.client.methods.HttpGet;
   import org.apache.http.client.methods.HttpPost;
   import org.apache.http.client.methods.HttpPut;
   import org.apache.http.entity.StringEntity;
   import org.apache.http.impl.client.BasicCredentialsProvider;
   import org.apache.http.impl.client.CloseableHttpClient;
   import org.apache.http.impl.client.HttpClients;
   import org.apache.http.util.EntityUtils;

.. code-block::

   public class CdmClient {
   private final static String DOMAIN_NAME=" account name";
   private final static String USER_NAME=" username";
   Private final static String USER_PASSWORD= "Password of the cloud user";
   private final static String PROJECT_ID="Project ID";
   private final static String CLUSTER_ID="CDM cluster ID";
   private final static String JOB_NAME="Job name";
   private final static String FROM_LINKNAME="Source link name";
   private final static String TO_LINKNAME="Destination link name";
   Private final static String IAM_ENDPOINT= "IAM endpoint";
   Private final static String CDM_ENDPOINT= "CDM endpoint";

.. code-block::

   private CloseableHttpClient httpclient;
   private String token;

   public CdmClient() {
   this.httpclient = createHttpClient();
   this.token = login();
   }

   private CloseableHttpClient createHttpClient() {
   CloseableHttpClient httpclient =HttpClients.createDefault();
   return httpclient;
   }

   private String login(){
   HttpPost httpPost = new HttpPost("https://"+IAM_ENDPOINT+"/v3/auth/tokens");
   String json =
   "{\r\n"+
   "\"auth\": {\r\n"+
   "\"identity\": {\r\n"+
   "\"methods\": [\"password\"],\r\n"+
   "\"password\": {\r\n"+
   "\"user\": {\r\n"+
   "\"name\": \""+USER_NAME+"\",\r\n"+
   "\"password\": \""+USER_PASSWORD+"\",\r\n"+
   "\"domain\": {\r\n"+
   "\"name\": \""+DOMAIN_NAME+"\"\r\n"+
   "}\r\n"+
   "}\r\n"+
   "}\r\n"+
   "},\r\n"+
   "\"scope\": {\r\n"+
   "\"project\": {\r\n"+
   "\"name\": \"PROJECT_NAME\"\r\n"+
   "}\r\n"+
   "}\r\n"+
   "}\r\n"+
   "}\r\n";
   try {
   StringEntity s = new StringEntity(json);
   s.setContentEncoding("UTF-8");
   s.setContentType("application/json");
   httpPost.setEntity(s);
   CloseableHttpResponse response = httpclient.execute(httpPost);
   Header tokenHeader = response.getFirstHeader("X-Subject-Token");
   String token = tokenHeader.getValue();
   System.out.println("Login successful");
   return token;
   } catch (Exception e) {
   throw new RuntimeException("login failed.", e);
   }
   }

.. code-block::

   /*Create a job.*/

   public void createJob(){
   HttpPost httpPost = new HttpPost("https://"+CDM_ENDPOINT+"/cdm/v1.0/"+PROJECT_ID+"/clusters/"+CLUSTER_ID+"/cdm/job");

   /**The JSON information here is complex. You can create a job on the job management page, click Job JSON Definition next to the job, copy the JSON content and convert it into a Java character string, and paste it here.
   *In the JSON message body, you only need to replace the link name, data import and export table names, field list of the tables, and fields used for partitioning in the source table.**/

   String json =
   "{\r\n"+
   "\"jobs\": [\r\n"+
   "{\r\n"+
   "\"from-connector-name\": \"generic-jdbc-connector\",\r\n"+
   "\"name\": \""+JOB_NAME+"\",\r\n"+
   "\"to-connector-name\": \"generic-jdbc-connector\",\r\n"+
   "\"driver-config-values\": {\r\n"+
   "\"configs\": [\r\n"+
   "{\r\n"+
   "\"inputs\": [\r\n"+
   "{\r\n"+
   "\"name\": \"throttlingConfig.numExtractors\",\r\n"+
   "\"value\": \"1\"\r\n"+
   "}\r\n"+
   "],\r\n"+
   "\"validators\": [],\r\n"+
   "\"type\": \"JOB\",\r\n"+
   "\"id\": 30,\r\n"+
   "\"name\": \"throttlingConfig\"\r\n"+
   "}\r\n"+
   "]\r\n"+
   "},\r\n"+
   "\"from-link-name\": \""+FROM_LINKNAME+"\",\r\n"+
   "\"from-config-values\": {\r\n"+
   "\"configs\": [\r\n"+
   "{\r\n"+
   "\"inputs\": [\r\n"+
   "{\r\n"+
   "\"name\": \"fromJobConfig.schemaName\",\r\n"+
   "\"value\": \"sqoop\"\r\n"+
   "},\r\n"+
   "{\r\n"+
   "\"name\": \"fromJobConfig.tableName\",\r\n"+
   "\"value\": \"city1\"\r\n"+
   "},\r\n"+
   "{\r\n"+
   "\"name\": \"fromJobConfig.columnList\",\r\n"+
   "\"value\": \"code&name\"\r\n"+
   "},\r\n"+
   "{\r\n"+
   "\"name\": \"fromJobConfig.partitionColumn\",\r\n"+
   "\"value\": \"code\"\r\n"+
   "}\r\n"+
   "],\r\n"+
   "\"validators\": [],\r\n"+
   "\"type\": \"JOB\",\r\n"+
   "\"id\": 7,\r\n"+
   "\"name\": \"fromJobConfig\"\r\n"+
   "}\r\n"+
   "]\r\n"+
   "},\r\n"+
   "\"to-link-name\": \""+TO_LINKNAME+"\",\r\n"+
   "\"to-config-values\": {\r\n"+
   "\"configs\": [\r\n"+
   "{\r\n"+
   "\"inputs\": [\r\n"+
   "{\r\n"+
   "\"name\": \"toJobConfig.schemaName\",\r\n"+
   "\"value\": \"sqoop\"\r\n"+
   "},\r\n"+
   "{\r\n"+
   "\"name\": \"toJobConfig.tableName\",\r\n"+
   "\"value\": \"city2\"\r\n"+
   "},\r\n"+
   "{\r\n"+
   "\"name\": \"toJobConfig.columnList\",\r\n"+
   "\"value\": \"code&name\"\r\n"+
   "}, \r\n"+
   "{\r\n"+
   "\"name\": \"toJobConfig.shouldClearTable\",\r\n"+
   "\"value\": \"true\"\r\n"+
   "}\r\n"+
   "],\r\n"+
   "\"validators\": [],\r\n"+
   "\"type\": \"JOB\",\r\n"+
   "\"id\": 9,\r\n"+
   "\"name\": \"toJobConfig\"\r\n"+
   "}\r\n"+
   "]\r\n"+
   "}\r\n"+
   "}\r\n"+
   "]\r\n"+
   "}\r\n";
   try {
   StringEntity s = new StringEntity(json);
   s.setContentEncoding("UTF-8");
   s.setContentType("application/json");
   httpPost.setEntity(s);
   httpPost.addHeader("X-Auth-Token", this.token);
   httpPost.addHeader("X-Language", "en-us");
   CloseableHttpResponse response = httpclient.execute(httpPost);
   int status = response.getStatusLine().getStatusCode();
   if(status == 200){
   System.out.println("Create job successful.");
   }else{
   System.out.println("Create job failed.");
   HttpEntity entity = response.getEntity();
   System.out.println(EntityUtils.toString(entity));
   }
   } catch (Exception e) {
   e.printStackTrace();
   throw new RuntimeException("Create job failed.", e);
   }
   }

.. code-block::

   /*Start the job.*/

   public void startJob(){
   HttpPut httpPut = new HttpPut("https://"+CDM_ENDPOINT+"/cdm/v1.0/"+PROJECT_ID+"/clusters/"+CLUSTER_ID+"/cdm/job/"+JOB_NAME+"/start");
   String json = "";
   try {
   StringEntity s = new StringEntity(json);
   s.setContentEncoding("UTF-8");
   s.setContentType("application/json");
   httpPut.setEntity(s);
   httpPut.addHeader("X-Auth-Token", this.token);
   httpPut.addHeader("X-Language", "en-us");
   CloseableHttpResponse response = httpclient.execute(httpPut);
   int status = response.getStatusLine().getStatusCode();
   if(status == 200){
   System.out.println("Start job successful.");
   }else{
   System.out.println("Start job failed.");
   HttpEntity entity = response.getEntity();
   System.out.println(EntityUtils.toString(entity));
   }
   } catch (Exception e) {
   e.printStackTrace();
   throw new RuntimeException("Start job failed.", e);
   }
   }

.. code-block::

   /*Query the job running status cyclically until the job is complete.*/

   public void getJobStatus(){
   HttpGet httpGet = new HttpGet("https://"+CDM_ENDPOINT+"/cdm/v1.0/"+PROJECT_ID+"/clusters/"+CLUSTER_ID+"/cdm/job/"+JOB_NAME+"/status");
   try {
   httpGet.addHeader("X-Auth-Token", this.token);
   httpGet.addHeader("X-Language", "en-us");
   boolean flag = true;
   while(flag){
   CloseableHttpResponse response = httpclient.execute(httpGet);
   int status = response.getStatusLine().getStatusCode();
   if(status == 200){
   HttpEntity entity = response.getEntity();
   String msg = EntityUtils.toString(entity);
   if(msg.contains("\"status\":\"SUCCEEDED\"")){
   System.out.println("Job succeeded");
   break;
   }else if (msg.contains("\"status\":\"FAILED\"")){
   System.out.println("Job failed.");
   break;
   }else{
   Thread.sleep(1000);
   }

   }else{
   System.out.println("Get job status failed.");
   HttpEntity entity = response.getEntity();
   System.out.println(EntityUtils.toString(entity));
   break;
   }
   }
   } catch (Exception e) {
   e.printStackTrace();
   throw new RuntimeException("Get job status failed.", e);
   }
   }

.. code-block::

   /*Delete the job.*/

   public void deleteJob(){
   HttpDelete httpDelte = new HttpDelete("https://"+CDM_ENDPOINT+"/cdm/v1.0/"+PROJECT_ID+"/clusters/"+CLUSTER_ID+"/cdm/job/"+JOB_NAME);
   try {
   httpDelte.addHeader("X-Auth-Token", this.token);
   httpDelte.addHeader("X-Language", "en-us");
   CloseableHttpResponse response = httpclient.execute(httpDelte);
   int status = response.getStatusLine().getStatusCode();
   if(status == 200){
   System.out.println("Delete job successful.");
   }else{
   System.out.println("Delete job failed.");
   HttpEntity entity = response.getEntity();
   System.out.println(EntityUtils.toString(entity));
   }
   } catch (Exception e) {
   e.printStackTrace();
   throw new RuntimeException("Delete job failed.", e);
   }
   }

.. code-block::

   /*Close the process.*/

   public void close(){
   try {
   httpclient.close();
   } catch (IOException e) {
   throw new RuntimeException("Close failed.", e);
   }
   }

   public static void main(String[] args){
   CdmClient cdmClient = new CdmClient();
   cdmClient.createJob();
   cdmClient.startJob();
   cdmClient.getJobStatus();
   cdmClient.deleteJob();
   cdmClient.close();
   }
   }
