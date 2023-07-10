:original_name: dataartsstudio_01_0499.html

.. _dataartsstudio_01_0499:

StringUtil Embedded Objects
===========================

A StringUtil embedded object provides methods of operating character strings, for example, truncating a substring from a character string.

StringUtil is implemented through org.apache.commons.lang3.StringUtils. For details about how to use the object, see the appache commons document.

**Example**
-----------

If variable a is character string No.0010, the substring after **.** is returned. The EL expression is as follows:

.. code-block::

   #{StringUtil.substringAfter(a,".")}
