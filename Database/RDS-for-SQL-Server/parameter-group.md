## Database > RDS for MS-SQL > Parameter Group

## Parameter group

RDS for MS-SQL provides the parameter group feature to apply the settings from the Microsoft SQL Server installed in the DB instance. A parameter group is a set of parameters that sets up the Microsoft SQL Server.
When the RDS for MS-SQL service is enabled, the basic parameter group `default.parameter-group` is provided. The basic parameter group cannot be deleted or changed.
A DB instance can use one parameter group, and the parameter group can be used by multiple DB instances at once.

### Parameter group status

The status of the parameter group consists of the following values and changes according to the user's actions and the current status.

| Status           | Description                                  |
|--------------|--------------------------------------|
| Applied | The parameter group has been applied to all DB instances associated with the parameter group |
| Applying | The parameter group is being applied to the DB instance |
| Need to Apply | The parameter group has been changed but not applied to DB instance |

### Creating or deleting a parameter group

A new parameter group can be created by copying an existing parameter group. The copied parameter group only copies parameters from the original parameter group and does not have any association with it.
The parameter group can be deleted only when no DB instance is using the parameter group; if there is a parameter group that is using it, it cannot be deleted.

## Parameters

Parameters have the following information:

* Name
  * Parameter name.
* Value
  * The value to be applied to the parameter.
* Permitted values
  * A range of values that can be applied to the parameter.
* Modifiable
  * Determines whether parameter can be modified.
* Applied type
  * Either `static` or `dynamic.`
  * If set to `Static,` the DB instance must be restarted to apply changes to the parameter.
  * If set to `Dynamic,` the parameter is applied immediately without DB instance restart.
* Data type
  * The type of the parameter value.

### Parameter variables, formulas, and functions

Certain parameters (e.g. `max server memory (mb)`) are better expressed as formulas that use values associated with the DB instance rather than static values. To support this, predefined variables, formulas, and functions can be used for the `numeric` data type.

* Formulas
  * `()`, `+`, `-`, `*`, `/` can be used.
  * The result of a formula must always be an integer, and decimal places are discarded.
* Functions
  * `max(a, b, ...)`: returns the largest in the array.
  * `min(a, b, ...)`: returns the smallest in the array.
* Variables
  * `ramSizeByte`: memory size of the current DB instance type (in bytes).
  * `storageSizeByte`: DB instance storage size (in bytes).

The below example is the default value of the `max server memory (mb)` parameter, and shows selecting 3/4 the memory size of the DB instance type:
```
ramSizeByte * 3 / 4 / 1048576
```

### Changing parameters

Only a parameter group created by users can be changed, and new one can be created by copying one from the existing parameter groups.
If parameters inside a parameter group are changed, the changes are applied simultaneously to all DB instances that are using the parameter group. If any of the DB instances using the parameter group is in the middle of processing some other tasks, the parameter won't be changed.
If applying the parameters to the DB instance fails, the changed parameters can be applied later.

There are two types of methods for applying parameters: `Dynamic` and `Static`.
A `Dynamic` parameter is applied immediately without restart when the parameter is changed.
A `Static` parameter is applied after a restart, and if any of the `Static` parameters are changed, `Waiting for restart` appears in the DB instance details page.

If the connection to the database is unavailable when parameters are changed, the database can be restarted.
Changing parameters for a DB instance in the connection unavailable status can fail. If the task is not completed properly, it will be reported to the administrator automatically, and NHN Cloud will contact you separately.

### Applying the updated parameters

You can update parameters for a DB instance to which the parameter group change has not been applied.
The procedure is performed in the same way as changing parameters, but it is applied only to the DB instance for which the user clicked Apply Updated Parameters.

