## Compute > Monitoring V2 > Overview 

Monitoring V2 provides improved monitoring features for user-created instances.  
You may check usage trends of system resources (CPU, memory, network, or disk), and set thresholds for major indicators to receive alarms on special situations by email or SMS. 

As resource usage information is collected by the agent process executed within an instance, it is more precise and additional monitoring indicators become available.  

To use this service, an instance must be created upon images where agent is provided as default.
An instance recording no history of agent installation must be installed manually. See the installation guide on the `Monitoring Tab of the Instance`.

## Main Features 


### Query Graphs on Monitoring Tab
Go to **Compute > Instance** in the TOAST console, and select an instance from the list. Check the graph on the **Monitoring** tab at the bottom of the screen. 

* Provide data which belongs to '1 hour ago - current (as of the current querying time)'
* Allow manual graph updates 


### Query Graphs of Integrated Monitoring  
Indicators for all instances selected by user for each graph are displayed.

* Specify a period to query data  
* Automatically update graphs (cycle setting is available)
* List of instances including detail information (instance can be selected)
* Query by a random field value from the list of instances 

### Query List of Alarms 
Alarm events can be queried. 

* List of events for alarms (including instances and situation information)
* Query alarm events during a configured period  
* Query alarm events by instance name or IP address 

### Manage Alarm Policy 
Set alarms for a variety of indicators or status, with instances specified.  

* Monitor non-delivered status of agent data  
* Monitor re-start of an instance 
* Set alarms for CPU usage 
* Set alarms for memory usage 
* Set alarms for disk space usage
* Set alarms for network transfer rate 
* Available to manage many alarm policies (an instance can be applied to one policy only) 
* Provide the list of alarm policies (along with summary for individual alarm policy)

### Set Receiving Alarms  
Recipients and the method of receiving alarms can be set. 

* Set alarm recipients  
* Choose the method of receiving alarms (by email or SMS) 
