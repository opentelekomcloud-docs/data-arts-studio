:original_name: dataartsstudio_01_0499.html

.. _dataartsstudio_01_0499:

StringUtil Embedded Objects
===========================

A StringUtil embedded object provides methods of operating character strings, for example, truncating a substring from a character string.

StringUtil is implemented through org.apache.commons.lang3.StringUtils. For details about how to use the object, see the `Apache Commons documentation <https://commons.apache.org/proper/commons-lang/apidocs/org/apache/commons/lang3/StringUtils.html>`__.

Example 1
---------

If variable a is character string No.0010, the substring after **.** is returned. The EL expression is as follows:

.. code-block::

   #{StringUtil.substringAfter(a,".")}

Example 2
---------

If variable b is string No,0020, the substring after **,** is returned. The EL expression is as follows:

.. code-block::

   #{StringUtil.split(b,',')[1]}

Example 3
---------

If the output of a node is a field, the output result is shown in [["000"]]. The second node references the output of the first node. In this case, the EL expression can be used to split the string result and obtain the field value output by the previous node.

.. code-block::

   #{StringUtil.split(StringUtil.split(StringUtil.split(Job.getNodeOutput("Name of the previous node"),"]")[0],"[")[0],"\\"")[0]}

Example 4
---------

If the output of the previous SQL node is [["11"]], the following EL expression can be used to obtain value "11":

#{StringUtil.getDigits(Job.getNodeOutput("nodeName"))}

Example 5
---------

Returns the digits extracted from a string.

String getDigits(String str)

For example, if str is "1123~45", "112345" is returned; if str is "abc", "" is returned; if str is "12345", "12345" is returned.
