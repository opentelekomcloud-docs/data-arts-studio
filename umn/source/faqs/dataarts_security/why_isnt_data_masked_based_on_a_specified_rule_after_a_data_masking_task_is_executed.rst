:original_name: dataartsstudio_03_0045.html

.. _dataartsstudio_03_0045:

Why Isn't Data Masked Based on a Specified Rule After a Data Masking Task Is Executed?
======================================================================================

Possible Causes
---------------

Static masking tasks depend on sensitive data discovery tasks. If the statuses of sensitive data fields were not changed to **Valid** on the **Sensitive Data Distribution** page, the system considers that there is no sensitive field, so does not mask data based on a rule.

Solution
--------

Before creating a static masking task, you must create a sensitive data discovery task. After sensitive fields are discovered, change the statuses of the sensitive fields to **Valid** on the **Sensitive Data Distribution** page.
