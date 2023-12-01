## Compute > System Monitoring > Advanced Monitoring(OpenMetrics) > Console Guide

Console Guide describes what are required to use Advanced Monitoring(OpenMetrics).
In **Compute > System Monitoring > OpenMetrics Dashboard**, you can define monitoring workspace and specify the collection target to collect random metrics that complies with the Exporter or its format.
Collected metrics can be checked by configuring a chart in a similar way as Server Dashboard.

## Workspace

The first thing you need to do to be able to use the Advanced Monitoring function is to create your workspace. You can define those that share the same monitoring purpose and of the same nature as a single workspace, and monitor the visualization method of the collection target and metrics.
Therefore, you need at least one workspace to be able to use the Advanced Monitoring.

### Create Workspace

To the left side of the dashboard screen, there is a workspace list. At the top of the list lies a text box for workspace search and a button that displays **Add Workspace** dialog.

Clicking the **Add** button brings up the **Add Workspace** dialog.
You can create this by entering a name, a description, and an URL Path in Workspace.
Name can contain alphanumeric characters, `-`, and `_`.
In URL Path, nothing else (Domain, Port, etc.) but only Path needs to be entered from the page address that provides metrics.

* Path Name Example

| Login Target                              | Entry Value            |
| ----------------------------------------- | ---------------------- |
| http://localhost:9100/metrics             | `/metrics`             |
| http://localhost:8080/actuator/prometheus | `/actuator/prometheus` |

### Modify/Delete Workspace

There is a gear icon to the right of each workspace in the workspace list displayed on the left side of the dashboard. Clicking the gear icon brings up the **Manage Workspace** dialog.

To modify this, enter a description and a URL Path and click the **modify** button.

To delete a workspace no longer used, click the **Delete** button.
Deleting the workspace also deletes all of its content including collection targets, layouts, and charts. However, if you create a new workspace of the same name, you can view previously collected metrics data.

## Collection Target

Once you created your workspace, now you have to specify the target to monitor. If you select a space from the workspace list to the left of the dashboard, the **Manage Collection Target** button appear at the top of the screen.
Clicking the **Manage Collection Target** button brings up a dialog that lets you add or delete collection targets.

### Add Collection Target

Above the **Manage Collection Target** dialog, a text box needed for adding monitoring targets is displayed.

Clicking the **Server** text box displays instances on which the agent of the System Monitoring works properly, and you can specify the target to collect by selecting one or more of them.

In the **Port** text box, enter the port of the Exporter or web application that provides metrics data.

Once Server and Port are typed in, click the **Add** button to add a target.
Currently, you can register up to 5 collection targets per server regardless of the classification of workspaces.

### View Collection Target

Under the **Manage Collection Target** dialog, the list of the collection targets registered for this workspace is displayed.
Status value is distinguished by color. For all collections except normal collection, a tooltip appears to provide more details when mouse is placed over any circle of those collections.

| Color  | Meaning                                                      |
| ------ | ------------------------------------------------------------ |
| Green  | Collecting normally                                          |
| Yellow | HTTP error response (404 Not Found, 503 Service Unavailable) |
| Red    | Collection disabled state (the port is not LISTEN or it is timed out) |
| Grey   | Preparing collection (right after collection targets are registered or the instance is stopped) |

> If the grey color does not change even after a while, please update the Agent with the latest version.
> ([How to install the Agent](https://docs.toast.com/zh/Compute/System%20Monitoring/zh/console-guide/#agent))
> If there is no change even after updating, please contact our Customer Center.

### Delete Collection Target

Below the list of the **Manage Collection Target** dialog, there is the **Delete** button. Select a target to delete in the checkbox left to the list and click **Delete** button to stop monitoring.

## Layout

Once workspace is created and collection target is specified, the Agent collects metrics and saves data in the System Monitoring system. To view the saved data, you need to configure a chart in the Layout. The Layout has a function similar to that of the Server Dashboard.

### Create Layout

If you want to visualize monitoring information by creating and place a chart in the dashboard, you can create a layout and then configure it to fit your needs.
To create a layout, click the **Create Layout** button above the dashboard. You can create up to 5 layouts per workspace.

Enter a name in the **Create Layout** dialog and click the **Create** button to generate a new layout. If there is no registered chart, a blank screen appears. To add a new chart, follow the on-screen instructions and click the **Add Chart** button.

### Modify/Delete Layout

By clicking the **Manage** button above the dashboard, you can change the name of a specific layout or delete unnecessary layouts.

## Chart

Unlike the Server Dashboard that lets users select one of the charts provided by the system, Advanced Monitoring dashboard allows users to directly specify the metrics and conditions that they want to show in their chart.

### Create Chart

To create a chart in the layout, click the **Add Chart** button above the dashboard.

In the **Add Chart** dialog, you can specify the chart name and Y-axis property of the chart, register metrics, and change the notification setting. The metrics and notification settings are placed under different tabs.
The left and right Y-axes can be separately enabled. You can specify a different unit for the value to display for each axis.
The enabled Y-axis is selected based on the grid displayed in the chart when metrics are added. Therefore, at least one of the two (left and right) must be enabled.
You can add multiple metrics. However, you need to add at least one metric. You can enter notification only when it is necessary.

#### Metrics

To add a metric, click the **Add Metrics** button in the **Metrics** tab.

Clicking the **Metrics** text box displays the list of the metrics currently being collected. You can select one from the list.

To the right of the Metrics text box, the list of Y-axis positions is displayed. Once a value from the list is selected, metrics are drawn on the chart based on the range of Y-axis in that position. If the values representing the metrics are outside the expression range of the Y-axis, the expression range is reset based on the biggest value from the metrics.

If there is a label for the selected metric, you can adjust **Filter** settings to look up only data that meets conditions by comparing the label values. Select one of the metric labels, and enter a value to compare with. You can specify a filter condition for multiple labels, but you cannot specify multiple filter conditions for the same label.


| Operator | Meaning                               | Example                                                      |
| -------- | ------------------------------------- | ------------------------------------------------------------ |
| `=`      | Match                                 | `mode = user`<br/>`mode` Displays only labels whose value is `user` |
| `!=`     | No match                              | `mode != idle`<br/>`mode` Displays only labels whose value is not `idle` |
| `=~`     | Matches the regular expression        | `code =~ 2.*`<br/>`code` Displays only labels whose value starts with `2` |
| `!~`     | Does not match the regular expression | `code !~ 5.*`<br/>`code` Displays only those labels whose value does not start with `5` |

If you enter a property for the metric and click the **Register** button, you can see if the data is being drawn as intended in the preview of the left chart.

#### Notification

To set up notification, click the **Add Notification** button in the **notification** tab.

To be able to distinguish the notification setting, enter **Name**, and then enter **Threshold** for the monitoring target. The specified threshold applied to all entries added as metrics for the chart. 
**Duration** determines whether an event has occurred or not based on the duration of the condition maintained. If Duration is set to '0,' at every cycle as soon as collected values meet the condition, the event is triggered.

In **Notification Group List**, you can select a notification group created in System Monitoring. Once an event occurs, the detail about the event occurrence is notified to the users in the group through the send channel specified for the group. However, the targets the notification group refers to are **Notification Type** and **User Group**, and monitoring setting or server list is irrelevant to the Advanced Monitoring.

If you enter each entry required for the notification settings and click the **Register** button, you will see the notification name added to the list.

After selecting metrics and notification settings, click the **Save** button under the **Add Chart** window to generate a chart.

### Modify Chart

By clicking the gear icon at the top right of each chart, you can modify the chart. In the **Add Chart** dialog, modify the one you want and then click the **modify** button.

### Delete Chart

By clicking the X icon at the top right of each chart, you can delete the chart. If you delete the chart, the notification settings enabled for the chart is also deleted.