# OpsMgr GenericServiceMonitoring ManagementPack

## Introduction:
It is often necessary to monitor windows services across your entire SCOM environment. This Management Pack gives you the ability to easily and quickly discover and monitor hundreds of services. The wildcard(*) notation allows great flexibility in discovering the services you are looking for.

This Management Pack is currently under development and may contain errors. Please always test it in DEV environment befor importing the Management Pack to production.

## Key Features

- wildcard(*) notation for servicenames
- one configuration for the entire management group

## Supported Environments

- System Center Operations Manager 2012 R2
- System Center Operations Manager Long Term Servicing Channel (2016)
- System Center Operations Manager Semi-Annual Channel (1807)

## How-To:
### 1. Import the Management Pack into SCOM.
### 2. Create the CSV file on one of your management server. 

   #### CSV file schema:

   __ServiceName;Include;Exclude__

    Include: comma-separated list of servernames (ShortName; not FQDN)

    Exclude: comma-separated list of servernames (ShortName; not FQDN)

    *: Every host in the "Microsoft.SystemCenter.ManagedComputerServer" class
    
   #### CSV file examples:
   
   __ServiceA;HostA,HostB;none__

    serviceA is monitored for hostA and hostB. There is no (none) exclusion.

  __ServiceB;*;none__

    serviceB is monitored on every host. There is no (none) exclusion.

  __Service*;*;HostB__

    service*(wildcard) is monitored on every host and excluded for hostB.


### 3. Start service ingestion task

   1. The task which starts the CSV ingestion process is found at the "Management Server View". Select the management server on which the CSV is located and execute the task. (example at Views -> State View Management Server)
   2. Click "Override" to enter the path to the CSV.
   
  ![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/RunTask.jpg)
  
   3. Enter the path to the CSV file.
   
  ![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/OverrideParameter.jpg)


### 4. Check discoverd services
The discovery is configured to run every 24h and detect newly processed services. This setting can be changed at the xml code to meet your requirements. So it can take up to 24 hours until the service can be discovered.

#### XML tag:
      <DataSource ID="DS" TypeID="Windows!Microsoft.Windows.TimedPowerShell.DiscoveryProvider">
 >      <IntervalSeconds>86400</IntervalSeconds>
       <SyncTime></SyncTime>
       <ScriptName>OpsMgr.GenericServiceMonitoring.Scripts.GetServicesToMonitor.Script.ps1</ScriptName>

## Views:

### State View Discoverd Services:
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Discovered%20Services.jpg)

### State View Management Server
![alt text](https://github.com/spa5603/OpsMgr.GenericServiceMonitoring/blob/master/Graphics/StateView%20-%20Management%20Server.jpg)

## Feedback
Please let me know if you have any problems or questions about the Management Pack. So don't hesitate to contact me via github or twitter @_pabstsebastian

## License Terms
OpsMgr GenericServiceMonitoring Copyright (C) 2018 Sebastian Pabst (spa5603)

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see http://www.gnu.org/licenses/.
