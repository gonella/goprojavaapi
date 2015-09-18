#How use the API - Simple example

##Simples example

```
//Getting the GoPro instance passing the credentials, the password is the gopro password.
//Dont forget you need to connect in gopro via wifi first. 
GoProApi gopro = new GoProApi("goprt4231");
//Starting a record in Go Pro
gopro.startRecord();
//Stopping a record in Go Pro
gopro.stopRecord();
//Stop record and then dispatch a power off operation against GoPro camera
gopro.stopRecordAndPowerOff();
//See more functions
GoProHelper helper = gopro.getHelper();
//helper.deleteFilesOnSd()
//Example how power on and start, wait some seconds and then stop with power off
for (int i = 0; i < 10; i++) {

        gopro.powerOnAndStartRecord();

        LogX.info("Waiting...." + 2 * _POLLINGTIME);
        Thread.sleep(2 * _POLLINGTIME);

        gopro.stopRecordAndPowerOff();
}
```
**This is a basic example to use the API, you can extend to call more functions. This is a simple abstraction.

##More URL to connect in GoPro

There are many commands available in GoPro, you just need to make a request to the camera, using the links below:
The cmd are dispatched against GoPro camera via HTTP request. 
The general query structure is  : http://<ip>/<device>/<app>?t=<password>&p=<command>
 Where:<device> can be bacpac or camera.
 
```
 From the page, we can extract the following queries;
 Turn on camera : http://<ip>/bacpac/PW?t=<password>&p=%01
Turn off camera : http://<ip>/bacpac/PW?t=<password>&p=
Change mode    : http://<ip>/bacpac/PW?t=<password>&p=%02
 Start capture : http://<ip>/bacpac/SH?t=<password>&p=%01
Stop capture : http://<ip>/bacpac/SH?t=<password>&p=
 Preview
On : http://<ip>/camera/PV?t=<password>&p=%02
Off : http://<ip>/camera/PV?t=<password>&p=
 Mode
Camera     : http://<ip>/camera/CM?t=<password>&p=
Photo        : http://<ip>/camera/CM?t=<password>&p=%01
Burst         : http://<ip>/camera/CM?t=<password>&p=%02
Timelapse : http://<ip>/camera/CM?t=<password>&p=%03
Timelapse : http://<ip>/camera/CM?t=<password>&p=%04
 Orientation
Head up     : http://<ip>/camera/UP?t=<password>&p=
Head down : http://<ip>/camera/UP?t=<password>&p=%01
 Video Resolution
WVGA-60  : http://<ip>/camera/VR?t=<password>&p=
WVGA-120  : http://<ip>/camera/VR?t=<password>&p=%01
720-30   : http://<ip>/camera/VR?t=<password>&p=%02
720-60   : http://<ip>/camera/VR?t=<password>&p=%03
960-30   : http://<ip>/camera/VR?t=<password>&p=%04
960-60   : http://<ip>/camera/VR?t=<password>&p=%05
1080-30 : http://<ip>/camera/VR?t=<password>&p=%06
 
FOV
wide : http://<ip>/camera/FV?t=<password>&p=
medium : http://<ip>/camera/FV?t=<password>&p=%01
narrow : http://<ip>/camera/FV?t=<password>&p=%02
 Photo Resolution
11mp wide     : http://<ip>/camera/PR?t=<password>&p=
8mp medium  : http://<ip>/camera/PR?t=<password>&p=%01
5mp wide       : http://<ip>/camera/PR?t=<password>&p=%02
5mp medium  : http://<ip>/camera/PR?t=<password>&p=%03
 Timer
0,5sec : http://<ip>/camera/TI?t=<password>&p=
1sec    : http://<ip>/camera/TI?t=<password>&p=%01
2sec    : http://<ip>/camera/TI?t=<password>&p=%02
5sec    : http://<ip>/camera/TI?t=<password>&p=%03
10sec  : http://<ip>/camera/TI?t=<password>&p=%04
30sec  : http://<ip>/camera/TI?t=<password>&p=%05
60sec  : http://<ip>/camera/TI?t=<password>&p=%06
 Localisation
On : http://<ip>/camera/LL?t=<password>&p=%01
Off : http://<ip>/camera/LL?t=<password>&p=
 Bip Volume
0%     : http://<ip>/camera/BS?t=<password>&p=
70%   : http://<ip>/camera/BS?t=<password>&p=%01
100% : http://<ip>/camera/BS?t=<password>&p=%02
```
