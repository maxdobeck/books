# Virtual Devices on Sauce Labs
{{ #include ../shared/appium-header.md }}

Please note that many commands and capabilities are iOS Simulator only. These typically cannot work on Real Devices and will also sometimes require a full simulator reboot. Or they must be set at runtime, when the Simulator launches.  For example

Execute Method `configureLocalization`: <https://appium.github.io/appium-xcuitest-driver/4.16/execute-methods/#mobile->



### Appium
#### iOS
Rely on the XCUI Driver capabilities. Read the [driver documentation and capability list](#ios-xcui-driver-notes).
Caps like [`appium:locale`](https://appium.github.io/appium-xcuitest-driver/4.16/capabilities/) are specifically for Simulators _"If a test is executed on a Simulator then UI locale is changed as well. You can also change Simulator locale in runtime using mobile: configureLocalization extension."_  


## Android UIAutomator 2 Driver Notes
{{ #include ../shared/android-header.md }}


## iOS XCUI Driver notes
{{#include ../shared/ios-header.md }}