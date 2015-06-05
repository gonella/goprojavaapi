Questions? Just put in the comments below:


## Simples examples ##

```

//Be sure that you are connected to GoPro WIFI connection before to proceed
			
//Getting the GoPro instance passing the credentials
GoProApi gopro = new GoProApi("goprt4231");
	
//Getting extra functions
GoProHelper helper = gopro.getHelper();
			
//With this function you will able to display the camera properties, like if the camera is ready to record or it is already power on.
BacPacStatus bacpacStatus = helper.getBacpacStatus();
			
//Just testing if the camera is ready to proceed with the record process.

int cameraReady = bacpacStatus.getCameraReady();
System.out.println("Camera ready 		? " + cameraReady);

if (ENCameraReady.READY.getCode() != cameraReady) {
throw new Exception(
					"The go pro is not ready. Check if it is power on.");
}

```