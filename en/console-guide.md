## Compute > Monitoring V2 > Console User Guide


## Query Status of Single Instance (from instance management)

Go to the TOAST console and select **Compute > Instance > Management**. Select `Instance to Query`. On the **Monitoring** tab below, you can query monitoring graphs of the instance. 

> [Notice]
> To enable this service for instances created before Monitoring V2 is provided, an agent must be installed in accordance with the installation guide on the **Monitoring** tab of the instance. <br>
> After agent is installed and graph shows on the **Monitoring** tab, then you can use Monitoring V2. 

All graphs show data during the `Last 1 Hour` as of the queried time, and automatic update is not available. 
Instead, click **Refresh** on the top left of the graph and check the latest data (manual update is available). 

![CPU usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_001.jpg) 

Each graph is described as below: 

| Graph |  Description  |
|:--------------|----------------|
|CPU Usage     | Total: Total CPU usage rate  (%)<br>sys: CPU usage required for the kernel mode (%)<br>usr: CPU usage required for the user mode (%) |
|Average CPU Load  | 1m: The average number of processes (including waiting status) using CPU for the last 1 minute <br>5m: The average number of processes (including waiting status) using CPU for the last 5 minutes <br>15m: The average number of processes (including waiting status) using CPU for the last 15 minutes <br><br> *[Note] This indicator is applied only for Linux instances. <br>(For Windows instances, graph shows but no data is provided.)* |
|Memory Usage  | Pused: Memory usage (%)<br>Swappused: Swap usage (%)<br><br>*[Note] In calculating Linux instance memory usage, buffer and cache areas are considered available, and not included to usage.* |
|Disk Usage    | IO: Disk device usage  (%)<br>Used: Disk space usage (%)<br><br>*[Note] IO and Used are provided for each mounted file system (disk drive for Windows) .* |
|Disk Transfer Rate    | Read: Transfer rate for read disk  (Bps)<br>Write: Transfer rate for write disk (Bps)<br><br>*[Note] Read and Write are provided for each mounted file system (disk drive for Windows).*<br>*[Note] Axis y is divided by Bps(Bytes per Sec), and the unit may change depending on the size of a value.* |
|Network Transfer Rate | In: Transfer rate for read network (Bps)<br>Out: Transfer rate for write network (Bps)<br><br>*[Note] In and Out are provided for each network device.*<br>*[Note] Axis y is divided by Bps(Bytes per Sec), and the unit may change depending on the size of a value.* |




## Query Status of Many Instances
Each graph of the **Server Details** tab (as below) shows indicators of a selected instance all at once. 
![server details image<](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_002.jpg)

### 1. List of Instances (arrow 1)
You can find the list of instances recording history of agent operations. 
> [Note]
> The list also includes those instances for which agent was operated but currently closed, as well as closed instances.   
> Such instances show 'InActive' status field. 

Selected instances are automatically reflected on the graphs (multiple selection is available). 

Basic information and resource usage of each instance (as of query/update time) are also available on the list of instances. 
>[Note]
>Read Disk or Write Disk on the list of instances refer to combined values of each indicator for all disks of an instance. 
>Network RX or Network TX on the list of instances refer to combined values of each indicator for all network devices of an instance. 

You can easily select targets by using search for all fields. 

### 2.Graphs (arrow 2)
Like the **Monitoring** tab, 6 graphs are provided; but here, each graph provides indicators of all selected instances at once. 

>[Note]
>The following two graphs provide only a part of indicators, unlike the **Monitoring** tab. <br>
>Graph on CPU Usage: Shows only the total usage of each instance
>Graph on Memory Usage: Shows only the memory usage (pused) of each instance 

Put the cursor on a graph and it points at an indicator value on its direction (axis x). 
And another graph without cursor also shows the indicator of the same direction (enabled by shared-tooltip). 

>[Note]
>Selecting many instances may cause low readability of graphs.   

### 3. Specify Query Periods (arrow 3)
Specify a query period of a graph to check status of instances during the period. 
> [Note]
> Graphs can be queried down to `Past 1 Year` as of the current time. 

| Setting Item | Description |
| ---------- | ----- |
| 1 hour  | Query data of the last 1 hour from the current time |
| 24 hour | Query data of the last 1 day from the current time |
| 1 week  | Query data of the last 1 week from the current time |
| 1 month | Query data of the last 1 month from the current time |
| Custom  | User specifies a querying period (start and closing time) |

### 4. Set Cycle of Graph Updates (arrow 4)
All graphs enable automatic 'Refresh'. 
When it is set 'off', the graph is not 'refreshed'. 
If it is not 'off', the graph is not 'refreshed' by the cycle of time when each value is displayed. 

## Set Alarm Policy 
On the **Alarm Setting** tab, you may query the list of alarm policy, or create ,modify, or delete each alarm policy. 

![alarm policy<](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_003.jpg)

Alarm policy contains settings to monitor instance status, and user can follow it to receive alarms on each instance status. 
>[Note]
>To receive alarms, [setting alarm recipients and method of receiving](./console-guide/#_4) is required. 

Monitoring V2 provides the `Default Policy`, which might be modified but cannot be deleted. 
>[Note]
>Instances immediately after monitoring service is registered (executed for an initial agent operation) are applied with the default policy. 
>Alarm policy to be applied for an instance can be changed any time. 

>[Caution]
>All instances can be included in only one policy. 
>When the alarm policy is deleted, all its instances belong to nowhere. 

Following items can be monitored under alarm policy: 
![alarm configuration<](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_004.jpg)

>[Note] Description of 'Setting Item' of the below table  <br>
> Enable: Set whether to enable each item (on/off)<br>
> Threshold: Minimum value to receive alarms for each item: warning or fatal <br>
> Duration: Time required to sustain status after an event is monitored due to settings of each item (Enable and Threshold) until when alarm is actually delivered (in other words, if a status changes within specified duration time, alarm is not raised.)<br>

| Monitoring Target | Setting Item | Purpose | Description |
|-----------|-----------|------|------|
| Reboot | Enable | Monitor if an instance is rebooted | Alarm is raised when instance rebooting is completed. <br><br>*[Note] Ignore`Reboot within 10 minutes`after alarm for reboot is sent  (do not send alarm)* |
| No Data | Enable<br>Duration |Monitor data non-delivery status of agent | Alarm is sent, if status is sustained during specified period of time set for Duration, ever since data non-delivery is initially detected |
| CPU | Enable<br>Threshold (warning, fatal)<br>Duration (warning, fatal) | Monitor CPU Usage (%) | Set threshold in two phases (warning and fatal) for the total CPU usage <br>Alarm is sent, if status is sustained even after duration, ever since specified threshold is reached. |
| Memory | Enable <br>Threshold (warning, fatal)<br>Duration (warning, fatal) | Monitor memory usage (%) | Set threshold in two phases (warning and fatal) for the memory usage <br>Alarms is sent, if status is sustained even after duration, ever since specified threshold is reached. |
| Disk Quota | Enable<br>Threshold (warning, fatal)<br>Duration (warning, fatal) | Monitor disk space usage (%) | Set threshold in two phases (warning and fatal) for the disk space usage <br>Alarm is sent, if status is sustained even after duration, ever since specified threshold is reached. <br><br>*[Note] To be applied individually, for many disks* |
| Network  | Enable <br>Threshold (warning, fatal)<br>Duration (warning, fatal) | Monitor network transfer rate (Bps) | Set threshold in two phases (warning and fatal) for the network transfer rate. <br>Alarm is sent, if status is sustained even after duration, ever since specified threshold is reached. <br><br>*[Note] To be applied individually, for many network devices. <br>*[Note] The threshold value refers to Network RX + TX (sum of the total receiving rate of individual network devices)* |
| List of Instances | Apply | Specify instances to apply policy | Apply policy-based monitoring to selected instances |


## Set Receiving Alarms 
You may set recipients and method of receiving alarms on the **Users** tab. 

![alarm user<](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_005.jpg)

Select a method of receiving alarms (by email or mobile phone) for a wanted user from the list, and press **Apply** to save the setting.   
Then, alarms are sent to the user in the specified method.  
To release alarm-receiving, take the same path and change settings. 

When it is detected to raise alarms for, an alarm message is delivered based on the setting.  
In addition, after initial alarm, additional alarms can be sent up to three times, upon the following criteria: 
(However, alarms for reboot are not applied.)

| When to Send Additional Alarms | Description |
| ----------| -----|
| After 10 Minutes | When status is sustained for more than 10 minutes, after initial alarm is sent |
| After 1 Hour | When status is sustained for more than 1 hour (60 minutes), after initial alarm is sent |
| After 1 Day | When status is sustained for more than a day (1440 minutes), after initial alarm is sent |

>[Note] OK Alarms 
> When an instance is back to normal status, it is notified by sending OK alarm once. 


## Query Alarm History  
Alarm history can be queried from the **Alarm Logs** tab. 
Each alarm history is created along with initial alarm delivery. 각 알람 이력은 알람을 최초로 발송했을 때 생성됩니다.

![alarm logs image<](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_006.jpg)

Alarm history is comprised of the following items:

| Item     | Description |
|--------------|-----------|
| Server Name | Name of an instance where alarm is raised |
| IP Address | IP address of an instance |
| Date     | Time when an alarm is sent |
| Measurement | Indicators for an alarm raised |
| Event Detection | Indicator values when an alarm is raised |
| Threshold | Threshold values specified for an indicator |
| Alarm Sending | Whether alarm is sent or not |

You may search by instance name or IP address, to check history of the instance. 
In addition, history during a particular period can be found by setting period.

> [Note]
> Alarms can be queried down to past 1 year as of the current time.  

| Button | Description |
|---------|-----------|
| 1 Day | Query alarm history during the past day, as of the current time |
| 1 Week | Query alarm history during the past week, as of the current time |
| 1 Month | Query alarm history during the past month, as of the current time |
| Specify | User specifies the period of time to query (start and end point of time) |


## Notes for Monitoring Agent 
| Item | Description |
| -----| -----|
| Data Collection Cycle | Monitoring agent collects and transfers data at every 1 minute. |
| Network-Port Configuration | For normal agent operations, TCP egress port 80 and 6600 must be allowed in the security group.  <br>There is no agent operational issue, when default security group of TOAST Compute is applied.<br>[Caution] If TCP egress port is designed by modifying security group, 80 and 6600 ports must be allowed. |
| Network - Internet Gateway Configuration | Internet gateway is required to deliver data collected by monitoring agent to a collector server. <br>There is no agent operational issue, when default TOAST Network setting is applied. <br>If Internet gateway is deleted, the instance monitoring service connected to the network cannot be enabled. |
| Suspension of Agent Process | When a running agent process is suspended, Monitoring V2 cannot be properly applied. |

If you are unable to use Monitoring V2 properly, contact [TOAST Customer Center](https://www.toast.com/support).

