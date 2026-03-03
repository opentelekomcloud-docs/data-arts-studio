:original_name: dataartsstudio_01_1038.html

.. _dataartsstudio_01_1038:

File Watermarks
===============

This section describes the following operations on file watermarks:

-  Insert invisible watermarks into structured data files (CSV, XML, and JSON files) and extract the watermarks.
-  Insert visible watermarks into unstructured data files (DOCX, PPTX, XLSX, and PDF files) and open the files on a local host to view the watermarks.

Constraints
-----------

-  Invisible watermarks can be inserted into and extracted from structured data files that are no longer than 4 MB.
-  Visible watermarks can be inserted into unstructured data files that are no longer than 20 MB.
-  Watermarks cannot be injected into files that already contain watermarks.
-  The data in structured data files into which watermarks are to be inserted must meet the following requirements:

   -  The source data must contain 5,000 or more lines. If the source data contains less than 5,000 lines, watermarks may fail to be extracted due to insufficient features.
   -  You are advised to select a column with various data values. If all the values of the column can be enumerated, the extraction may fail due to insufficient features. Common columns that can be embedded with watermarks include the address, name, UUID, amount, and total amount.
   -  If a watermark is inserted into a numeric integer field, the data may be modified. Insert watermarks into a field whose value can be changed.

-  Watermark extraction from structured data files is irrelevant to the source tracing tasks using data watermarks. Only users under the same account can extract watermarks from structured data files into which watermarks have been inserted by following the instructions in :ref:`Inserting a Watermark <dataartsstudio_01_1038__en-us_topic_0000001629752668_section1595913533918>` or :ref:`Dynamic Watermarks <dataartsstudio_01_1039>`.

.. _dataartsstudio_01_1038__en-us_topic_0000001629752668_section1595913533918:

Inserting a Watermark
---------------------

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **File Watermarks**.


   .. figure:: /_static/images/en-us_image_0000002269120233.png
      :alt: **Figure 1** Accessing the File Watermarks page

      **Figure 1** Accessing the File Watermarks page

#. Set the parameters listed in :ref:`Table 1 <dataartsstudio_01_1038__en-us_topic_0000001629752668_table179731221105915>`.

   .. _dataartsstudio_01_1038__en-us_topic_0000001629752668_table179731221105915:

   .. table:: **Table 1** Parameters for inserting a watermark

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                 |
      +===================================+=============================================================================================================================================+
      | \*Data Type                       | Select a file type.                                                                                                                         |
      |                                   |                                                                                                                                             |
      |                                   | -  **Structured data**: CSV, XML, and JSON. You can insert an invisible watermark into a file and extract the watermark.                    |
      |                                   | -  **Unstructured data**: DOCX, PPTX, XLSX, and PDF You can insert a visible watermark into a file and open the file to view the watermark. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | **Structured data**               |                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Watermark Content               | Watermark ID that will be embedded by the system into data tables. The watermark ID can contain a maximum of 16 characters.                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data                            | CSV, XML, or JSON files are supported.                                                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Field                           | Fields into which the watermark is to be inserted.                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | **Unstructured data**             |                                                                                                                                             |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Watermark Content               | Watermark ID that will be embedded by the system into data tables. The watermark ID can contain a maximum of 16 characters.                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Transparency                      | Transparency of the plaintext watermark                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Rotation Angle                    | Rotation angle of the plaintext watermark                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | Font Size                         | Font size of the plaintext watermark                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data                            | DOCX, PPTX, XLSX, and PDF files are supported.                                                                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Insert Watermark**. The browser automatically downloads the inserted file.

   You can click **Reset** to restore the parameters to default settings.

.. _dataartsstudio_01_1038__en-us_topic_0000001629752668_section23271629153418:

Extracting a Watermark
----------------------

You can extract invisible watermarks that have been inserted into structured data files in CSV, XML, or JSON format. For details about watermark insertion, see :ref:`Inserting a Watermark <dataartsstudio_01_1038__en-us_topic_0000001629752668_section1595913533918>`.

#. On the DataArts Studio console, locate a workspace and click **DataArts Security**.

#. In the left navigation pane, choose **File Watermarks**. In the right pane, click the **Watermark Extraction** tab.


   .. figure:: /_static/images/en-us_image_0000002234081024.png
      :alt: **Figure 2** Accessing the Watermark Extraction page

      **Figure 2** Accessing the Watermark Extraction page

#. Set the parameters listed in :ref:`Table 2 <dataartsstudio_01_1038__en-us_topic_0000001629752668_table73288293345>`.

   .. _dataartsstudio_01_1038__en-us_topic_0000001629752668_table73288293345:

   .. table:: **Table 2** Parameters for extracting a watermark

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================+
      | \*Data Type                       | File type. Only CSV, XML, and JSON are supported.                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                    |
      |                                   | You can insert an invisible watermark into a file of any preceding type and extract the watermark.                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Watermark Content               | You do not need to set this parameter. The extracted watermark will be automatically displayed.                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \*Data                            | Select the structured data file in CSV, XML, or JSON format into which an invisible watermark has been inserted based on :ref:`Inserting a Watermark <dataartsstudio_01_1038__en-us_topic_0000001629752668_section1595913533918>`. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Extract Watermark**. The extracted watermark is displayed in the **Watermark Content** parameter.

   You can click **Reset** to restore the parameters to default settings.
