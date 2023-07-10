:original_name: dataartsstudio_03_0201.html

.. _dataartsstudio_03_0201:

What Is the Priority of the Startup User, Execution User, Workspace Agency, and Job Agency?
===========================================================================================

The system obtains permissions for the job agency, workspace agency, and execution user in sequence, and then executes jobs with the permissions.

By default, a job is executed by the user who starts the job. If a job is started by a user with low permissions, the job will fail to be executed due to insufficient permissions. To resolve this issue, you can configure an agency or an execution user.

-  After an agency is configured for a job, the job interacts with other services through the agency, preventing job execution failures caused by permission issues. There are two types of agencies, workspace agencies and job agencies. Workspace agencies have a higher priority than job agencies.

   -  Workspace agency: applies to all the jobs in a workspace. You can choose **Configuration** > **Configure** > **Agency** to configure a workspace agency.
   -  Job agency: applies to a single job. You can configure a job agency in the basic information of a job.

-  After an execution user is configured, the user will be used to start the job. You can configure an execution user in the basic information of a job.
