:original_name: dataartsstudio_01_0106.html

.. _dataartsstudio_01_0106:

Regular Expressions for Separating Semi-structured Text
=======================================================

During table/file migration, CDM uses delimiters to separate fields in CSV files. However, delimiters cannot be used in complex semi-structured data because the field values also contain delimiters. In this case, the regular expression can be used to separate the fields.

The regular expression is configured in **Source Job Configuration**. The migration source must be an object storage or file system, and **File Format** must be **CSV**.


.. figure:: /_static/images/en-us_image_0000001373168645.jpg
   :alt: **Figure 1** Setting regular expression parameters

   **Figure 1** Setting regular expression parameters

During the migration of CSV files, CDM can use regular expressions to separate fields and write parsed results to the migration destination. For details about the syntax of the regular expression, refer to the related documents. This section describes the regular expressions of the following log files:

-  :ref:`Log4J Log <dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section3640870614023>`
-  :ref:`Log4J Audit Log <dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section3778456914559>`
-  :ref:`Tomcat Log <dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section20618611495>`
-  :ref:`Django Log <dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section1163361141018>`
-  :ref:`Apache Server Log <dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section61918911141058>`

.. _dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section3640870614023:

Log4J Log
---------

-  Log sample:

   .. code-block::

      2018-01-11 08:50:59,001 INFO  [org.apache.sqoop.core.SqoopConfiguration.configureClassLoader(SqoopConfiguration.java:251)] Adding jars to current classloader from property: org.apache.sqoop.classpath.extra

-  Regular expression:

   .. code-block:: text

      ^(\d.*\d) (\w*)  \[(.*)\] (\w.*).*

-  Parsing result:

   .. table:: **Table 1** Log4J log parsing result

      +---------------+--------------------------------------------------------------------------------------------+
      | Column Number | Example Value                                                                              |
      +===============+============================================================================================+
      | 1             | 2018-01-11 08:50:59,001                                                                    |
      +---------------+--------------------------------------------------------------------------------------------+
      | 2             | INFO                                                                                       |
      +---------------+--------------------------------------------------------------------------------------------+
      | 3             | org.apache.sqoop.core.SqoopConfiguration.configureClassLoader(SqoopConfiguration.java:251) |
      +---------------+--------------------------------------------------------------------------------------------+
      | 4             | Adding jars to current classloader from property: org.apache.sqoop.classpath.extra         |
      +---------------+--------------------------------------------------------------------------------------------+

.. _dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section3778456914559:

Log4J Audit Log
---------------

-  Log sample:

   .. code-block::

      2018-01-11 08:51:06,156 INFO  [org.apache.sqoop.audit.FileAuditLogger.logAuditEvent(FileAuditLogger.java:61)] user=sqoop.anonymous.user    ip=189.xxx.xxx.75    op=show    obj=version    objId=x

-  Regular expression:

   .. code-block:: text

      ^(\d.*\d) (\w*)  \[(.*)\] user=(\w.*)    ip=(\w.*)    op=(\w.*)    obj=(\w.*)    objId=(.*).*

-  Parsing result:

   .. table:: **Table 2** Log4J audit log parsing result

      +---------------+-------------------------------------------------------------------------------+
      | Column Number | Example Value                                                                 |
      +===============+===============================================================================+
      | 1             | 2018-01-11 08:51:06,156                                                       |
      +---------------+-------------------------------------------------------------------------------+
      | 2             | INFO                                                                          |
      +---------------+-------------------------------------------------------------------------------+
      | 3             | org.apache.sqoop.audit.FileAuditLogger.logAuditEvent(FileAuditLogger.java:61) |
      +---------------+-------------------------------------------------------------------------------+
      | 4             | sqoop.anonymous.user                                                          |
      +---------------+-------------------------------------------------------------------------------+
      | 5             | 189.xxx.xxx.75                                                                |
      +---------------+-------------------------------------------------------------------------------+
      | 6             | show                                                                          |
      +---------------+-------------------------------------------------------------------------------+
      | 7             | version                                                                       |
      +---------------+-------------------------------------------------------------------------------+
      | 8             | x                                                                             |
      +---------------+-------------------------------------------------------------------------------+

.. _dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section20618611495:

Tomcat Log
----------

-  Log sample:

   .. code-block::

      11-Jan-2018 09:00:06.907 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log OS Name:               Linux

-  Regular expression:

   .. code-block:: text

      ^(\d.*\d) (\w*) \[(.*)\] ([\w\.]*) (\w.*).*

-  Parsing result:

   .. table:: **Table 3** Tomcat log parsing result

      ============= =====================================================
      Column Number Example Value
      ============= =====================================================
      1             11-Jan-2018 09:00:06.907
      2             INFO
      3             main
      4             org.apache.catalina.startup.VersionLoggerListener.log
      5             OS Name:Linux
      ============= =====================================================

.. _dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section1163361141018:

Django Log
----------

-  Log sample:

   .. code-block::

      [08/Jan/2018 20:59:07 ] settings     INFO     Welcome to Hue 3.9.0

-  Regular expression:

   .. code-block:: text

      ^\[(.*)\] (\w*)     (\w*)     (.*).*

-  Parsing result:

   .. table:: **Table 4** Django log parsing result

      ============= ====================
      Column Number Example Value
      ============= ====================
      1             08/Jan/2018 20:59:07
      2             settings
      3             INFO
      4             Welcome to Hue 3.9.0
      ============= ====================

.. _dataartsstudio_01_0106__en-us_topic_0000001197659215_en-us_topic_0000001197658803_en-us_topic_0108275466_section61918911141058:

Apache Server Log
-----------------

-  Log sample:

   .. code-block::

      [Mon Jan 08 20:43:51.854334 2018] [mpm_event:notice] [pid 36465:tid 140557517657856] AH00489: Apache/2.4.12 (Unix) OpenSSL/1.0.1t configured -- resuming normal operations

-  Regular expression:

   .. code-block:: text

      ^\[(.*)\] \[(.*)\] \[(.*)\] (.*).*

-  Parsing result:

   .. table:: **Table 5** Apache server log parsing result

      +---------------+---------------------------------------------------------------------------------------+
      | Column Number | Example Value                                                                         |
      +===============+=======================================================================================+
      | 1             | Mon Jan 08 20:43:51.854334 2018                                                       |
      +---------------+---------------------------------------------------------------------------------------+
      | 2             | mpm_event:notice                                                                      |
      +---------------+---------------------------------------------------------------------------------------+
      | 3             | pid 36465:tid 140557517657856                                                         |
      +---------------+---------------------------------------------------------------------------------------+
      | 4             | AH00489: Apache/2.4.12 (Unix) OpenSSL/1.0.1t configured -- resuming normal operations |
      +---------------+---------------------------------------------------------------------------------------+
