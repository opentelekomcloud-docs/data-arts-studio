:original_name: dataartsstudio_01_0534.html

.. _dataartsstudio_01_0534:

Loop Embedded Objects
=====================

You can use Loop embedded objects to obtain data from the For Each dataset.

Property
--------

.. table:: **Table 1** Property description

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Property              | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | dataArray             | String                | Dataset input by the For Each node. It is a two-dimensional array.      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | current               | String                | Data row traversed by the For Each node. It is a one-dimensional array. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | offset                | Int                   | Current offset of the For Each node, starting from 0.                   |
   |                       |                       |                                                                         |
   |                       |                       | Loop.dataArray[Loop.offset] = Loop.current.                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

Example
-------

The EL expression for the Foreach operator to cyclically obtain the first column of the output (a two-dimensional array) of the previous node is as follows:

.. code-block::

   #{Loop.current[0]}
