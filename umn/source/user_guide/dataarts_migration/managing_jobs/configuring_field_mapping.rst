:original_name: dataartsstudio_01_0261.html

.. _dataartsstudio_01_0261:

Configuring Field Mapping
=========================

Scenario
--------

-  After the job parameters are configured, you can configure field mapping. You can click |image1| on the **Map Field** page to customize new fields or click |image2| in the **Operation** column to create a field converter.
-  If files are migrated between FTP, SFTP, OBS, and HDFS and the migration source's **File Format** is set to **Binary**, files will be directly transferred, free from field mapping.
-  In other scenarios, CDM automatically maps fields of the source table and the destination table. You need to check whether the mapping and time format are correct. For example, check whether the source field type can be converted into the destination field type.
-  In the auto table creation scenario, you need to add fields to the destination table in advance, and add the fields to the field mapping.

Constraints
-----------

-  If **Use SQL Statement** is set to **Yes** in the source job configuration, converters cannot be created.

-  On the **Map Field** tab page, if CDM fails to obtain all columns by obtaining sample values (for example, when data is exported from HBase, CloudTable, or MongoDB, there is a high probability that CDM failed to obtain all columns), you can click |image3| and select **Add a new field** to add new fields to ensure that the data imported to the migration destination is complete.
-  When a relational database, Hive, DLI, or MRS Hudi is used as the migration source, sample values cannot be obtained.
-  When SQLServer is the destination, fields of the timestamp type cannot be written. You must change their type (for example, to datetime) so that they can be written.
-  Column names are displayed when the source of the migration job is OBS, CSV files are to be migrated, and parameter **Extract first row as columns** is set to **Yes**.
-  Field mapping is not involved when the binary format is used to migrate files to files.
-  In the automatic table creation scenario, you need to manually add fields to the destination table in advance and then add fields to the field mapping.
-  After a field is added, its sample value is not displayed on the console. This does not affect the field value transmission. CDM directly writes the field value to the destination end.
-  If the field mapping is incorrect, you can adjust the field mapping by dragging fields or clicking |image4| to map fields in batches.
-  If the data is imported to DWS, you need to select the distribution columns in the destination fields. You are advised to select the distribution columns according to the following principles:

   #. Use the primary key as the distribution column.
   #. If multiple data segments are combined as primary keys, specify all primary keys as the distribution column.
   #. In the scenario where no primary key is available, if no distribution column is selected, DWS uses the first column as the distribution column by default. As a result, data skew risks exist.

-  If a source field type is not supported, convert the field type to a type supported by CDM by referring to :ref:`Converting Unsupported Data Types <dataartsstudio_01_0209>`.

Adding a Field
--------------

You can click |image5| on the **Map Field** page and select **Add** to customize a new field. This field is usually used to mark the database source to ensure the integrity of the data imported to the migration destination.


.. figure:: /_static/images/en-us_image_0000002305406377.png
   :alt: **Figure 1** Field mapping

   **Figure 1** Field mapping

Currently, the following field types are supported:

-  **Constant Parameter**

   Constant parameters are fixed parameters and do not need to be reconfigured. For example, **lable** = **friends** is used to identify a constant value.

-  **Variables**

   You can use variables such as time macros, table name macros, and version macros to mark database source information. The variable syntax is ${variable}, where **variable** indicates a variable. For example, **input_time** = **${timestamp()}** indicates the timestamp of the current time.

-  Expression

   You can use the expression language to dynamically generate parameter values based on the running environment. The expression syntax is #{expr}, where **expr** indicates an expression. For example, **time** = **#{DateUtil.now()}** is used to identify the current date string.

Creating a Converter
--------------------

CDM supports field conversion. Click |image6| and then click **Create Converter**.


.. figure:: /_static/images/en-us_image_0000002305439409.png
   :alt: **Figure 2** Creating a converter

   **Figure 2** Creating a converter

CDM can convert fields during migration. Currently, the following field converters are supported:

-  **Anonymization**

   This converter is used to hide key information about the character string. For example, if you want to convert **12345678910** to **123****8910**, configure the parameters as follows:

   -  Set **Reserve Start Length** to **3**.
   -  Set **Reserve End Length** to **4**.
   -  Set **Replace Character** to **\***.

-  **Trim**

   This converter is used to automatically delete the spaces before and after a string. No parameters need to be configured.

-  **Reverse string**

   This converter is used to automatically reverse a string. For example, reverse **ABC** into **CBA**. No parameters need to be configured.

-  **Replace string**

   This converter is used to replace a character string. You need to configure the object to be replaced and the new value.

-  **Remove line break**

   This converter is used to delete the newline characters, such as \\n, \\r, and \\r\\n from the field.

-  **Expression conversion**

   This converter uses the JSP expression language (EL) to convert the current field or a row of data. The JSP EL is used to create arithmetic and logical expressions. Within a JSP EL expression, you can use integers, floating point numbers, strings, the built-in constants **true** and **false** for boolean values, and **null**.

   -  The expression supports the following environment variables:

      -  **value**: indicates the current field value.
      -  **row**: indicates the current row, which is an array type.

   -  The expression supports the following Utils:

      #. If the field is of the string type, convert all character strings into lowercase letters, for example, convert **aBC** to **abc**.

         Expression: StringUtils.lowerCase(value)

      #. Convert all character strings of the current field to uppercase letters.

         Expression: StringUtils.upperCase(value)

      #. Convert the format of the first date field from 2018-01-05 15:15:05 to 20180105.

         Expression: DateUtils.format(DateUtils.parseDate(row[0],"yyyy-MM-dd HH:mm:ss"),"yyyyMMdd")

      #. Convert a timestamp to a date string in *yyyy-MM-dd hh:mm:ss* format, for example, convert **1701312046588** to **2023-11-30 10:40:46**.

         Expression: DateUtils.format(NumberUtils.toLong(value),"yyyy-MM-dd HH:mm:ss")

      #. Convert a date string in the yyyy-MM-dd hh:mm:ss format to a timestamp.

         Expression: DateUtils.getTime(DateUtils.parseDate(value,"yyyy-MM-dd hh:mm:ss"))

      #. If the field value is a date string in *yyyy-MM-dd* format, extract the year from the field value, for example, extract **2017** from **2017-12-01**.

         Expression: StringUtils.substringBefore(value,"-")

      #. If the field value is of the numeric type, convert the value to a new value which is two times greater than the original value:

         Expression: value*2

      #. Convert the field value **true** to **Y** and other field values to **N**.

         Expression: value=="true"?"Y":"N"

      #. If the field value is of the string type and is left empty, convert it to **Default**. Otherwise, the field value will not be converted.

         Expression: empty value? "Default":value

      #. Convert date format **2018/01/05 15:15:05** to **2018-01-05 15:15:05**:

         Expression: DateUtils.format(DateUtils.parseDate(value,"yyyy/MM/dd HH:mm:ss"),"yyyy-MM-dd HH:mm:ss")

      #. Obtain a 36-bit universally unique identifier (UUID):

         Expression: CommonUtils.randomUUID()

      #. If the field is of the string type, capitalize the first letter, for example, convert **cat** to **Cat**.

         Expression: StringUtils.capitalize(value)

      #. If the field is of the string type, convert the first letter to a lowercase letter, for example, convert **Cat** to **cat**.

         Expression: StringUtils.uncapitalize(value)

      #. If the field is of the string type, use a space to fill in the character string to the specified length and center the character string. If the length of the character string is not shorter than the specified length, do not convert the character string. For example, convert **ab** to meet the specified length 4.

         Expression: StringUtils.center(value,\ *4*)

      #. Delete a newline (including **\\n**, **\\r**, and **\\r\\n**) at the end of a character string. For example, convert **abc\\r\\n\\r\\n** to **abc\\r\\n**.

         Expression: StringUtils.chomp(value)

      #. If the string contains the specified string, **true** is returned; otherwise, **false** is returned. For example, **abc** contains **a** so that **true** is returned.

         Expression: StringUtils.contains(value,"*a*")

      #. If the string contains any character of the specified string, **true** is returned; otherwise, **false** is returned. For example, **zzabyycdxx** contains either **z** or **a** so that **true** is returned.

         Expression: StringUtils.containsAny(value,"*za*")

      #. If the string does not contain any one of the specified characters, **true** is returned. If any specified character is contained, **false** is returned. For example, **abz** contains one character of **xyz** so that **false** is returned.

         Expression: StringUtils.containsNone(value,"*xyz*")

      #. If the string contains only the specified characters, **true** is returned. If any other character is contained, **false** is returned. For example, **abab** contains only characters among **abc** so that **true** is returned.

         Expression: StringUtils.containsOnly(value,"*abc*")

      #. If the character string is empty or null, convert it to the specified character string. Otherwise, do not convert the character string. For example, convert the empty character string to null.

         Expression: StringUtils.defaultIfEmpty(value,\ *null*)

      #. If the string ends with the specified suffix (case sensitive), **true** is returned; otherwise, **false** is returned. For example, if the suffix of **abcdef** is not null, **false** is returned.

         Expression: StringUtils.endsWith(value,\ *null*)

      #. If the string is the same as the specified string (case sensitive), **true** is returned; otherwise, **false** is returned. For example, after strings **abc** and **ABC** are compared, **false** is returned.

         Expression: StringUtils.equals(value,"*ABC*")

      #. Obtain the first index of the specified character string in a character string. If no index is found, **-1** is returned. For example, the first index of **ab** in **aabaabaa** is 1.

         Expression: StringUtils.indexOf(value,"*ab*")

      #. Obtain the last index of the specified character string in a character string. If no index is found, **-1** is returned. For example, the last index of **k** in **aFkyk** is 4.

         Expression: StringUtils.lastIndexOf(value,"*k*")

      #. Obtain the first index of the specified character string from the position specified in the character string. If no index is found, **-1** is returned. For example, the first index of **b** obtained after the index 3 of **aabaabaa** is 5.

         Expression: StringUtils.indexOf(value,"*b*",\ *3*)

      #. Obtain the first index of any specified character in a character string. If no index is found, **-1** is returned. For example, the first index of **z** or **a** in **zzabyycdxx.** is 0.

         Expression: StringUtils.indexOfAny(value,"*za*")

      #. If the string contains any Unicode character, **true** is returned; otherwise, **false** is returned. For example, **ab2c** contains only non-Unicode characters so that **false** is returned.

         Expression: StringUtils.isAlpha(value)

      #. If the string contains only Unicode characters and digits, **true** is returned; otherwise, **false** is returned. For example, **ab2c** contains only Unicode characters and digits, so that **true** is returned.

         Expression: StringUtils.isAlphanumeric(value)

      #. If the string contains only Unicode characters, digits, and spaces, **true** is returned; otherwise, **false** is returned. For example, **ab2c** contains only Unicode characters and digits, so that **true** is returned.

         Expression: StringUtils.isAlphanumericSpace(value)

      #. If the string contains only Unicode characters and spaces, **true** is returned; otherwise, **false** is returned. For example, **ab2c** contains Unicode characters and digits so that **false** is returned.

         Expression: StringUtils.isAlphaSpace(value)

      #. If the string contains only printable ASCII characters, **true** is returned; otherwise, **false** is returned. For example, for **!ab-c~**, **true** is returned.

         Expression: StringUtils.isAsciiPrintable(value)

      #. If the string is empty or null, **true** is returned; otherwise, **false** is returned.

         Expression: StringUtils.isEmpty(value)

      #. If the string contains only Unicode digits, **true** is returned; otherwise, **false** is returned.

         Expression: StringUtils.isNumeric(value)

      #. Obtain the leftmost characters of the specified length. For example, obtain the leftmost two characters **ab** from **abc**.

         Expression: StringUtils.left(value,\ *2*)

      #. Obtain the rightmost characters of the specified length. For example, obtain the rightmost two characters **bc** from **abc**.

         Expression: StringUtils.right(value,\ *2*)

      #. Concatenate the specified character string to the left of the current character string and specify the length of the concatenated character string. If the length of the current character string is not shorter than the specified length, the character string will not be converted. For example, if **yz** is concatenated to the left of **bat** and the length must be 8 after concatenation, the character string is **yzyzybat** after conversion.

         Expression: StringUtils.leftPad(value,\ *8*,"*yz*")

      #. Concatenate the specified character string to the right of the current character string and specify the length of the concatenated character string. If the length of the current character string is not shorter than the specified length, the character string will not be converted. For example, if **yz** is concatenated to the right of **bat** and the length must be 8 after concatenation, the character string is **batyzyzy** after conversion.

         Expression: StringUtils.rightPad(value,\ *8*,"*yz*")

      #. If the field is of the string type, obtain the length of the current character string. If the character string is null, **0** is returned.

         Expression: StringUtils.length(value)

      #. If the field is of the string type, delete all the specified character strings from it. For example, delete **ue** from **queued** to obtain **qd**.

         Expression: StringUtils.remove(value,"*ue*")

      #. If the field is of the string type, remove the substring at the end of the field. If the specified substring is not at the end of the field, no conversion is performed. For example, remove **.com** at the end of **www.domain.com**.

         Expression: StringUtils.removeEnd(value,"*.com*")

      #. If the field is of the string type, delete the substring at the beginning of the field. If the specified substring is not at the beginning of the field, no conversion is performed. For example, delete **www.** at the beginning of **www.domain.com**.

         Expression: StringUtils.removeStart(value,"*www.*")

      #. If the field is of the string type, replace all the specified character strings in the field. For example, replace **a** in **aba** with **z** to obtain **zbz**.

         Expression: StringUtils.replace(value,"*a*","*z*")

      #. If the field is of the string type, replace multiple characters in the character string at a time. For example, replace **h** in **hello** with **j** and **o** with **y** to obtain **jelly**.

         Expression: StringUtils.replaceChars(value,"*ho*","*jy*")

      #. If the string starts with the specified prefix (case sensitive), **true** is returned; otherwise, **false** is returned. For example, **abcdef** starts with **abc**, so that **true** is returned.

         Expression: StringUtils.startsWith(value,"*abc*")

      #. If the field is of the string type, delete all the specified characters at the beginning and end of the field. the field. For example, delete all **x**, **y**, **z**, and **b** from **abcyx** to obtain **abc**.

         Expression: StringUtils.strip(value,"*xyz*\ b")

      #. If the field is of the string type, delete all the specified characters at the end of the field, for example, delete the **abc** string at the end of the field.

         Expression: StringUtils.stripEnd(value,\ *"abc"*)

      #. If the field is of the string type, delete all the specified characters at the beginning of the field, for example, delete all spaces at the beginning of the field.

         Expression: StringUtils.stripStart(value,\ *null*)

      #. If the field is of the string type, obtain the substring after the specified position (the index starts from 0, including the character at the specified position) of the character string. If the specified position is a negative number, calculate the position in the descending order. The first digit at the end is -1. For example, obtain the second character (c) of **abcde** and the string after it, that is, **cde**.

         Expression: StringUtils.substring(value,\ *2*)

      #. If the field is of the string type, obtain the substring in a specified range (the index starts from 0, including the character at the start and excluding the character at the end). If the range is a negative number, calculate the position in the descending order. The first digit at the end is -1. For example, obtain the string between the second character (c) and fourth character (e) of **abcde**, that is, **cd**.

         Expression: StringUtils.substring(value,\ *2*,4)

      #. If the field is of the string type, obtain the substring after the first specified character. For example, obtain the substring after the first **b** in **abcba**, that is, **cba**.

         Expression: StringUtils.substringAfter(value,"*b*")

      #. If the field is of the string type, obtain the substring after the last specified character. For example, obtain the substring after the last **b** in **abcba**, that is, **a**.

         Expression: StringUtils.substringAfterLast(value,"*b*")

      #. If the field is of the string type, obtain the substring before the first specified character. For example, obtain the substring before the first **b** in **abcba**, that is, **a**.

         Expression: StringUtils.substringBefore(value,"*b*")

      #. If the field is of the string type, obtain the substring before the last specified character. For example, obtain the substring before the last **b** in **abcba**, that is, **abc**.

         Expression: StringUtils.substringBeforeLast(value,"*b*")

      #. If the field is of the string type, obtain the substring nested within the specified string. If no substring is found, **null** is returned. For example, obtain the substring between **tag** in **tagabctag**, that is, **abc**.

         Expression: StringUtils.substringBetween(value,"*tag*")

      #. If the field is of the string type, delete the control characters (char<=32) at both ends of the character string, for example, delete the spaces at both ends of the character string.

         Expression: StringUtils.trim(value)

      #. Convert the character string to a value of the byte type. If the conversion fails, **0** is returned.

         Expression: NumberUtils.toByte(value)

      #. Convert the character string to a value of the byte type. If the conversion fails, the specified value, for example, **1**, is returned.

         Expression: NumberUtils.toByte(value,\ *1*)

      #. Convert the character string to a value of the double type. If the conversion fails, **0.0d** is returned.

         Expression: NumberUtils.toDouble(value)

      #. Convert the character string to a value of the double type. If the conversion fails, the specified value, for example, **1.1d**, is returned.

         Expression: NumberUtils.toDouble(value,\ *1.1d*)

      #. Convert the character string to a value of the float type. If the conversion fails, **0.0f** is returned.

         Expression: NumberUtils.toFloat(value)

      #. Convert the character string to a value of the float type. If the conversion fails, the specified value, for example, **1.1f**, is returned.

         Expression: NumberUtils.toFloat(value,\ *1.1f*)

      #. Convert the character string to a value of the int type. If the conversion fails, **0** is returned.

         Expression: NumberUtils.toInt(value)

      #. Convert the character string to a value of the int type. If the conversion fails, the specified value, for example, **1**, is returned.

         Expression: NumberUtils.toInt(value,\ *1*)

      #. Convert the character string to a value of the long type. If the conversion fails, **0** is returned.

         Expression: NumberUtils.toLong(value)

      #. Convert the character string to a value of the long type. If the conversion fails, the specified value, for example, **1L**, is returned.

         Expression: NumberUtils.toLong(value,\ *1L*)

      #. Convert the character string to a value of the short type. If the conversion fails, **0** is returned.

         Expression: NumberUtils.toShort(value)

      #. Convert the character string to a value of the short type. If the conversion fails, the specified value, for example, **1**, is returned.

         Expression: NumberUtils.toShort(value,\ *1*)

      #. Convert the IP string to a value of the long type, for example, convert **10.78.124.0** to **172915712**.

         Expression: CommonUtils.ipToLong(value)

      #. Read an IP address and physical address mapping file from the network, and download the mapping file to the map collection. *url* indicates the address for storing the IP mapping file, for example, **http://10.114.205.45:21203/sqoop/IpList.csv**.

         Expression: HttpsUtils.downloadMap("*url*")

      #. Cache the IP address and physical address mappings and specify a key for retrieval, for example, **ipList**.

         Expression: CommonUtils.setCache("*ipList*",HttpsUtils.downloadMap("*url*"))

      #. Obtain the cached IP address and physical address mappings.

         Expression: CommonUtils.getCache("*ipList*")

      #. Check whether the IP address and physical address mappings are cached.

         Expression: CommonUtils.cacheExists("*ipList*")

      #. Based on the specified offset type (month/day/hour/minute/second) and offset (positive number indicates increase and negative number indicates decrease), convert the time in the specified format to a new time, for example, add 8 hours to **2019-05-21 12:00:00**.

         Expression: DateUtils.getCurrentTimeByZone("*yyyy-MM-dd HH:mm:ss*",value, "*hour*", *8*)

      #. If the value is empty or null, "aaa" is returned. Otherwise, **value** is returned.

         Expression: StringUtils.defaultIfEmpty(value,\ *"aaa"*)

Special Links
-------------

-  If the source link is a DLI link, and the destination link is a DWS link, fields of the tinyint type of the DLI link are mapped to fields of the smallint type of the DWS link.
-  If the source link is a Hudi link, and the destination link is a DWS link, fields of the Double type of the Hudi link are mapped to fields of the Float type of the DWS link.

.. |image1| image:: /_static/images/en-us_image_0000002270789624.png
.. |image2| image:: /_static/images/en-us_image_0000002305439425.png
.. |image3| image:: /_static/images/en-us_image_0000002305439429.png
.. |image4| image:: /_static/images/en-us_image_0000002270846502.png
.. |image5| image:: /_static/images/en-us_image_0000002270846498.png
.. |image6| image:: /_static/images/en-us_image_0000002270846494.png
