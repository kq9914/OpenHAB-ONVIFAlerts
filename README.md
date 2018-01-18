# OpenHAB-ONVIFAlerts

#### What is this?
it's a script utilizing the guts of [hicknotify](https://github.com/ccontavalli/hicknotify) by ccontavalli to integrate ONVIF cameras (primarily Hikvision) with OpenHAB by setting an OpenHAB contact object to "OPEN" when a video motion detector event is detected by the camera.

Take a look at the hicknotify readme for more information on dampening, etc... a lot of the functionality in the original script was removed so that the logic could be done in OpenHAB rather than in the script.

#### Example with one camera and video motion detection alerts triggering the OpenHAB contact VMD_FrontDoor to OPEN when motion is detected.  
```json
{
   "Cameras":[
      {
         "Url":"http://192.168.1.121/ISAPI/Event/notification/alertStream",
         "Name":"Front Door",
         "Username":"admin",
         "Password":"12345",
         "VMDAlarmEnable":true,
         "LineCrossAlarmEnable":false,
         "IOAlarmEnable":false,
         "VMDTarget":"VMD_FrontDoor",
         "LineCrossTarget":"",
         "IOAlarmTarget":""
      }
   ],
   "DampeningTime":30,
   "WatchdogTime":10,
   "ErrorRetryTime":5,
   "OpenHABHost":"192.168.1.110:8080",
   "OpenHABBasicAuth":true,
	 "OpenHABUsername":"user1",
	 "OpenHABPassword":"password123"
}
```
#### How to use
build the go file and then put config.json in the same directory as the executable 
