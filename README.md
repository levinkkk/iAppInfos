iAppInfos
=========

iAppInfos allows a easy access to ALL important App informations.  

![Image](demo.png)

# Device infos
*   iOS Version 
*   Device model
*   Free Disk Space
*   Battery Level 

# Apps infos
*   Targeted iOS Version
*   Version number 
*   Short Version number
*   SDK use for compilation
*   Mobile provisionning push information (enable or not),
*   Mobile provisionning dev information (development / production),
*   Mobile provisionning UDID list (provisioned devices),

# Optionnal keys
*   WS Configuration
*   Token push

# Configuration

To configure iAppInfos, you can set a custom datasource
```objective-c
[AppInformationsManager sharedManager].datasource = self;
```
## Add customs key/values

```objective-c
[[AppInformationsManager sharedManager] addCustomValue:@"This is a custom value" forCustomKey:@"CustomKey1"];
```

## Configure interest keys

Your datasource can optionally implement desiredKeysForAppVersionManager method to filter the keys you need to observe.

```objective-c

- (NSArray *)desiredKeysForAppVersionManager:(AppInformationsManager *)manager
{
    return @[AppVersionManagerKeyYouriOSVersion,AppVersionManagerKeyYourDeviceModel,AppVersionManagerKeyCompilationSDK, AppVersionManagerKeyCFBundleVersion, AppVersionManagerKeyFreeDiskSpace, AppVersionManagerKeyBatteryLevel,AppVersionManagerKeyMobileProvisionning, AppVersionManagerKeyPushToken,AppVersionManagerKeyWSConfiguration];
}
```
## WS / Token configuration  

Your datasource can optionally implements this 2 methods to help the Manager to find this 2 values.

+ getWSConfigurationForAppVersionManager
+ getpushTokenForAppVersionManager

# Usage in the real life 

See the sample, a very classic TableView Controller (JMOViewController)


