:original_name: dataartsstudio_03_0133.html

.. _dataartsstudio_03_0133:

What Should I Do If the Background Reports an Error When I Access the Test App Through the Data Service API and Set Related Parameters?
=======================================================================================================================================

Possible Causes
---------------

The header parameter is not set.

Solution
--------

Set the header parameter when invoking the API.

.. code-block::

   header parameter: x-Authorization, nvalid ___ parameter: ___,
