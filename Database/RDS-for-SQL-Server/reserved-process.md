## Database > RDS for MS-SQL > Scheduled Task

You can view, modify, or delete the created scheduled tasks.

## Scheduled Task

A scheduled task function is provided so that a specific task can be started at a desired time. The scheduled task runs at the task schedule time, but is not guaranteed to be completed within the task schedule time.

### Scheduled Task Status

The status types of scheduled tasks are as follows:

| Status         | Description                                      |
|------------|-----------------------------------------|
| Scheduled        | The task has been scheduled, before it is task schedule time.                   |
| Registered        | The state before the task starts, when it is task schedule time.                  |
| Running       | The scheduled task is in progress.                                |
| Done        | The scheduled task has been completed normally.                     |
| Deleted        | The scheduled task has been deleted.                          |
| Cancellation Requested    | Cancellation has been requested while the scheduled task is in progress.                |
| Force Cancellation Requested | Forced cancellation has been requested when the scheduled task is in progress.             |
| Canceling       | The scheduled task has been canceled and the task required for cancellation is in progress.     |
| Canceled       | The scheduled task has been canceled normally.                            |
| Error         | The scheduled task failed for an unknown reason.                |
| Validation Failed | Validation failed because the DB instance has changed since the scheduled task was created. |

### Schedule Time Type

The following are the types of schedule time that can be selected when editing a scheduled task.

| Schedule Time Type | Description                               |
|----------|----------------------------------|
| Repeated Daily    | The system tries starting a scheduled task repeatedly every day at the set time. |
| After Specific Time | The system starts a scheduled task after a specific time.            |
