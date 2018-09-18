# OpsMgr GenericServiceMonitoring ManagementPack

## Introduction:
It is often necessary to monitor windows services across your entire SCOM environment. This ManagementPack processes the services, provided by CSV and detects them into their own class. Service wildcard is also possible.

## Configuration:
##### 1. CSV File Layout:

__ServiceName;Include;Exclude__

Include: Comma separated List of Servername(ShortName)

Exclude: Comma separated List of Servername(ShortName)

*: Every Host in the "Microsoft.SystemCenter.ManagedComputerServer" Class

**ServiceA;HostA,HostB;none**

ServiceA is monitored for HostA and HostB. There is no exclusion.

**ServiceB;*;none**

ServiceB is monitored on every Host. There is no exclusion.

__Service*;*;HostB__

Service*(wildcard) is monitored on every Host and excluded for HostB.


##### 2. Start Sevice Ingest Task

__Execute Task__

  1. The Task which starts the CSV ingestion process in found at the "Management Server View". Select the MS on which the CSV is located      and execute the Task. (Views -> State View Management Server)
  2. Click "Override" to enter the path to the CSV.
  ![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/RunTask.jpg)
  
  3. Enter the path to the CSV file.
  ![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/OverrideParameter.jpg)


##### 3 .Check discoverd Services

## Examples:

## Views:

##### State View Discoverd Services:
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Discovered%20Services.jpg)

##### State View Management Server
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Management%20Server.jpg)
