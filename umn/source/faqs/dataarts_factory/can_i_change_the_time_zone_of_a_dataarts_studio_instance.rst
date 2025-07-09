:original_name: dataartsstudio_03_0193.html

.. _dataartsstudio_03_0193:

Can I Change the Time Zone of a DataArts Studio Instance?
=========================================================

Currently, the time zone of a DataArts Studio instance cannot be changed.

During the scheduling of data development jobs, an EL expression can be used to adapt to the local time. The following is an example EL expression:

.. code-block::

   #{DateUtil.format(DateUtil.addHours(Job.planTime,-7),"yyyy-MM-dd")}
