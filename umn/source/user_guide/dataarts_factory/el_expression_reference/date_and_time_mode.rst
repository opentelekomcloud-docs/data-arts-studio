:original_name: dataartsstudio_01_0496.html

.. _dataartsstudio_01_0496:

Date and Time Mode
==================

The date and time in the EL expression can be displayed in a user-specified format. The date and time format is specified by the date and time mode character string. The date and time mode character string consists of letters from A to Z and from a to z, as shown in :ref:`Table 1 <dataartsstudio_01_0496__en-us_topic_0132998733_table5464612155214>`.

.. _dataartsstudio_01_0496__en-us_topic_0132998733_table5464612155214:

.. table:: **Table 1** Letter description

   ====== ========================= ====================================
   Letter Description               Example
   ====== ========================= ====================================
   G      Epoch                     AD
   y      Year                      2001
   M      Month in a year           July or 07
   d      Day in a month            10
   h      Hour in the 12-hour clock 12
   H      Hour in the 24-hour clock 22
   m      Minute                    30
   s      Second                    55
   S      Millisecond               234
   E      Day of a week             Mon, Tue, Wed, Thu, Fri, Sat, or Sun
   D      Date in the year          360
   F      Day in a week of a month  2(second Wed. in July)
   w      Week in a year            40
   W      Week in a month           1
   a      A.M. /P.M.                PM
   k      Hour in the 24-hour clock 24
   K      Hour in the 12-hour clock 10
   z      Time zone                 Eastern Standard Time
   '      Text delimiter            None
   "      Single quotation mark     No example
   ====== ========================= ====================================

Example
-------

To obtain the date of the day before the planned scheduling time of a job, use the following EL expression:

.. code-block::

   #{DateUtil.format(DateUtil.addDays(Job.planTime,-1),"yyyy-MM-dd")}
