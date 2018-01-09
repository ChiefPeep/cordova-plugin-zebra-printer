# zbtprinter
A Cordova/Phonegap driver for Zebra bluetooth printers

This is a fork of https://github.com/diegorquera/zbtprinter.git

Update version ZSDK_ANDROID_API.jar and permissions.

## Usage
You can find Zebra printer using:

```
window.cordova.plugins.zbtprinter.find(
    function(result) {
        if(typeof result == 'string') {
            address = result;
        } else {
            address = result.address;
        }
        alert('Zbtprinter: connect success: ' + address);
    }, function(error) {
        alert('Zbtprinter: connect fail: ' + error);
    }
);
```

You can send data in ZPL Zebra Programing Language:

```
window.cordova.plugins.zbtprinter.print(address, "^XA^FO20,20^A0N,25,25^FDThis is a ZPL test.^FS^XZ",
    function(success) {
        alert("Zbtprinter print success: " + success);
    }, function(fail) {
        alert("Zbtprinter print fail:" + fail);
        deferred.reject(fail);
    }
);
```

You can get a status response from a connected Zebra printer using:

```
window.cordova.plugins.zbtprinter.getStatus(address,
    function(success){
        alert("Zbtprinter status: " + success);
    }, function(fail) {
        alert("Zbtprinter error: " + fail);
    }
);
```

## Install Cordova

```
cordova plugin add https://github.com/ChiefPeep/cordova-plugin-zebra-printer.git
```

## ZPL - Zebra Programming Language
For more information about ZPL please see the  [PDF Official Manual](https://support.zebra.com/cpws/docs/zpl/zpl_manual.pdf)
