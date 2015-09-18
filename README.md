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
