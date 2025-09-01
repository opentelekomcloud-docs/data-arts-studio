:original_name: dataartsstudio_03_0620.html

.. _dataartsstudio_03_0620:

What Should I Do If a Message Is Displayed Indicating that the ID Does Not Exist During the Execution of a DWS SQL Script?
==========================================================================================================================

Possible Causes
---------------

This issue is caused by the case of the ID.

Solution
--------

During the execution of a DWS SQL script, the system uses lowercase letters by default. If a field is in upper case, add "".

Example: select \* from *table1* order by "ID";

.. code-block::

   select * from table order by "ID";
