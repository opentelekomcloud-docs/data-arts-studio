:original_name: dataartsstudio_03_0016.html

.. _dataartsstudio_03_0016:

What Should I Do If Database or Table Information Cannot Be Obtained Through a GaussDB(DWS)/Hive/HBase Data Connection?
=======================================================================================================================

Possible Causes
---------------

The possible cause is that the CDM cluster is stopped or a concurrency conflict occurs. You can switch to another agent to temporarily avoid this issue.

Solution
--------

To resolve this issue, perform the following steps:

#. Check whether the CDM cluster is stopped.

   -  If yes, start the CDM cluster and check whether the data connection in Management Center recovers.
   -  If no, go to :ref:`step 2 <dataartsstudio_03_0016__li3276134385818>`.

#. .. _dataartsstudio_03_0016__li3276134385818:

   Check whether the CDM cluster is used as an agent for both a data migration job and a data connection in Management Center.

   -  If yes, do not use the data migration job and the data connection at the same time, or create another CDM cluster as an agent for the data migration job and the data connection.
   -  If no, go to :ref:`step 3 <dataartsstudio_03_0016__li6276104395818>`.

#. .. _dataartsstudio_03_0016__li6276104395818:

   Restart the CDM cluster to release resources and check whether the data connection recovers.
