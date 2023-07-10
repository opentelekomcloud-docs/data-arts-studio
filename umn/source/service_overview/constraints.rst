:original_name: dataartsstudio_07_006.html

.. _dataartsstudio_07_006:

Constraints
===========

Browser Restrictions
--------------------

The following table lists the recommended browser for logging in to DataArts Studio.

.. table:: **Table 1** Browser compatibility

   =========================== ===========
   Browser Version             Description
   =========================== ===========
   Google Chrome 93.x or later Recommended
   =========================== ===========

Use Restrictions
----------------

Before using DataArts Studio, you must read and understand the following restrictions:

#. DataArts Studio is a one-stop platform that provides data integration, development, and governance capabilities. DataArts Studio has no storage or computing capability and relies on the data lake base.
#. Different components of DataArts Studio support different data sources. You need to select a data lake base based on your service requirements. For details about the data lakes supported by DataArts Studio, see :ref:`Data Sources Supported by DataArts Studio <dataartsstudio_01_0005__section1818582902919>`.
#. For details about the constraints on DataArts Migration, see **DataArts Migration** > **Constraints** in the *DataArts Studio User Guide*.

Reliability Restrictions
------------------------

To achieve high reliability in using DataArts Studio, you are advised to understand the following restrictions and measures:

#. The DataArts Migration cluster is deployed in standalone mode. A cluster fault may cause service and data loss. You are advised to use the CDM Job node of DataArts Factory to invoke CDM jobs and select two CDM clusters to improve reliability. For details, see **DataArts Factory** > **Nodes** > **CDM Job** in the *DataArts Studio User Guide*.
#. You can enable automatic backup and restoration of CDM jobs. Backups of CDM jobs are stored in OBS buckets. For details, see **DataArts Migration** > **Job Management** > **Job Configuration Management** in the *DataArts Studio User Guide*.
#. You can enable scheduled backup of assets such as scripts and jobs to OBS buckets, and restore assets from their backups. For details, see **DataArts Factory** > **O&M and Scheduling** > **Managing Backups** in the *DataArts Studio User Guide*.
