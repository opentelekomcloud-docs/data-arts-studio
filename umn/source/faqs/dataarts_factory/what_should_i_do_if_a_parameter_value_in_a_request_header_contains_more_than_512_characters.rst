:original_name: dataartsstudio_03_0619.html

.. _dataartsstudio_03_0619:

What Should I Do If a Parameter Value in a Request Header Contains More Than 512 Characters?
============================================================================================

The Rest Client operator is used as an example.

Symptom
-------

When configuring a parameter for a job operator, you need to enter the parameter name and value. If you already enter 512 characters for the parameter value, you cannot enter more characters.


.. figure:: /_static/images/en-us_image_0000002270845678.png
   :alt: **Figure 1** Configuring a request header parameter

   **Figure 1** Configuring a request header parameter

Solution
--------

#. Configure a request header parameter for the job node.

   Enter a variable name for **Value**, for example, **{para}**.


   .. figure:: /_static/images/en-us_image_0000002305438625.png
      :alt: **Figure 2** Configuring a request header parameter

      **Figure 2** Configuring a request header parameter

#. Configure job parameters.

   a. Click **Parameter Setup**.

   b. Enter variable **para** and its value. The value can contain a maximum of 1,024 characters.


      .. figure:: /_static/images/en-us_image_0000002270845686.png
         :alt: **Figure 3** Configuring job parameters

         **Figure 3** Configuring job parameters

      The preceding method resolves the length issue of the request header parameter value.
