# Locale: Virtual Devices
Locale is not GeoLocation. Locale is usually the operating region of the device, aka what the user would select when booting the phone. This may be hard locked into the device but depends on the model and OS. Defer to the Appropriate system settings + developer info.

Third party code may be critical in managing internationalization testing. [Locale & Region](https://support.apple.com/en-gb/guide/iphone/iphce20717a3/ios#:~:text=You%20choose%20the%20language%20and,%3E%20General%20%3E%20Language%20%26%20Region.) impact things like currency characters, temperature values, calendar format, what the first day of the week is (sunday or monday), and other culturally significant values. 

Be aware your app may disregard the region setting in the device (Android/iOS) and defer to the cellular region, GPS Location, and/or the IP address. You may have to check with your development team to determine how location and locale is determined by the app.


## Android UIAutomator 2 Driver Notes
{{ #include ../shared/android-header.md }}

## iOS XCUI Driver Notes
{{ #include ../shared/ios-header.md }}


