:original_name: dataartsstudio_01_0497.html

.. _dataartsstudio_01_0497:

Env Embedded Objects
====================

An Env embedded object provides a method of obtaining an environment variable value.

Method
------

.. table:: **Table 1** Method description

   +-------------------------+--------------------------------------------------------+
   | Method                  | Description                                            |
   +=========================+========================================================+
   | String get(String name) | Obtains the value of a specified environment variable. |
   +-------------------------+--------------------------------------------------------+

Example
-------

The EL expression used to obtain the value of environment variable **test** is as follows:

.. code-block::

   #{Env.get("test")}
