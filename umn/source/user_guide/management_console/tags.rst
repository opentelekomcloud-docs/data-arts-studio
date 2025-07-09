:original_name: en-us_topic_0000002270788944.html

.. _en-us_topic_0000002270788944:

Tags
====

A tag is a key-value pair that identifies an instance. It consists of a key and a value.

DataArts Studio instance tags can be used in the following scenarios:

-  If there are a large number of cloud resources, you can add tags to them (including DataArts Studio instances) by user, maintainer, or usage. Then you can use Tag Management Service (TMS) to identify tags and manage cloud resources easily.
-  If there are multiple DataArts Studio instances, you can add tags to them by user, maintainer, or usage. Then you can search for and identify DataArts Studio instances by tag on the DataArts Studio instance list page.

Constraints
-----------

-  A DataArts Studio instance can have a maximum of 20 tags.
-  Each tag key must be unique. Only one tag value can be added to a tag key.

Procedure
---------

#. Log in to the DataArts Studio console by following the instructions in :ref:`Accessing the DataArts Studio Instance Console <dataartsstudio_01_0001>`.

#. On the **Tags** page, click **Add/Edit Tag**. In the displayed dialog box, set parameters. Enter a tag key and a value, and click **Add**.


   .. figure:: /_static/images/en-us_image_0000002270790648.png
      :alt: **Figure 1** Adding/Editing tags

      **Figure 1** Adding/Editing tags

   .. table:: **Table 1** Tag parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================================================================================================================================================+
      | Tag Key                           | DataArts Studio supports predefined tags and resource tags.                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  Predefined tags are created on TMS. They may suit your needs to manage multiple services by tag.                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    To use a predefined tag, you must create one on TMS first. Then you can select it from the **Tag key** drop-down list. You can click **View predefined tags** to enter the **Predefined Tag** page of TMS. Then, click **Create Tag** to create a predefined tag. For details, see *Creating Predefined Tags* in *Tag Management Service User Guide*. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  Resource tags are created when you add a tag. You do not need to define them in advance. Resource tags are suitable for you to manage DataArts Studio instances by tag.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    To use a resource tag, you can enter the tag key in the box. The tag key can contain a maximum of 128 characters, including uppercase letters, lowercase letters, digits, spaces, and the following special characters: ``_.:=+-@.`` The tag key cannot start with a space or **\_sys\_**, or end with a space.                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag Value                         | You can specify the tag value in either of the following ways:                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  Predefined tags: Click the text box and select a predefined tag value from the drop-down list.                                                                                                                                                                                                                                                        |
      |                                   | -  Resource tags: Enter a tag value in the text box. The tag value can contain a maximum of 255 characters, including uppercase letters, lowercase letters, digits, spaces, and the following special characters: ``_.:=+-@.`` The tag value cannot start or end with a space.                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
