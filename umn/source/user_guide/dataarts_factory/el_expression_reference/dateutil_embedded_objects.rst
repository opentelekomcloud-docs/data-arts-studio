:original_name: dataartsstudio_01_0500.html

.. _dataartsstudio_01_0500:

DateUtil Embedded Objects
=========================

A DateUtil embedded object provides methods of formatting time and calculating time.

Methods
-------

.. table:: **Table 1** Method description

   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                                     | Description                                                                                                                                                       |
   +============================================+===================================================================================================================================================================+
   | String format(Date date, String pattern)   | Formats Date to character strings according to the specified pattern.                                                                                             |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date addMonths(Date date, int amount)      | After the specified number of months is added to Date, the new Date object is returned. The amount can be a negative number.                                      |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date addDays(Date date, int amount)        | After the specified number of days is added to Date, the new Date object is returned. The amount can be a negative number.                                        |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date addHours(Date date, int amount)       | After the specified number of hours is added to Date, the new Date object is returned. The amount can be a negative number.                                       |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date addMinutes(Date date, int amount)     | After the specified number of minutes is added to Date, the new Date object is returned. The amount can be a negative number.                                     |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | int getDay(Date date)                      | Obtains the day from the date. For example, if the date is 2018-09-14, 14 is returned.                                                                            |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | int getMonth(Date date)                    | Obtains the month from the date. For example, if the date is 2018-09-14, 9 is returned.                                                                           |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | int getYear(Date date)                     | Obtains the year from the date. For example, if the date is 2018-09-14, 2018 is returned.                                                                         |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date now()                                 | Returns the current time.                                                                                                                                         |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | long getTime(Date date)                    | Converts the date type to the long type.                                                                                                                          |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Date parseDate(String str, String pattern) | Converts the character string to the date by pattern. The pattern is the date and time mode. For details, see :ref:`Date and Time Mode <dataartsstudio_01_0496>`. |
   +--------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Example**
-----------

The previous day of the job scheduling plan time is used as the subdirectory name to generate an OBS path. The EL expression is as follows:

.. code-block::

   #{"obs://test/"+DateUtil.format(DateUtil.addDays(Job.planTime,-1),"yyyy-MM-dd")}
