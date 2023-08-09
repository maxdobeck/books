# Virtual Devices on Sauce Labs
{{ #include ../shared/appium-header.md }}

### Appium
#### iOS
Rely on the XCUI Driver capabilities. Read the [driver documentation and capability list](#ios-xcui-driver-notes).
Caps like [`appium:locale`](https://appium.github.io/appium-xcuitest-driver/4.16/capabilities/) are specifically for Simulators _"If a test is executed on a Simulator then UI locale is changed as well. You can also change Simulator locale in runtime using mobile: configureLocalization extension."_  


## Android UIAutomator 2 Driver Notes
{{ #include ../shared/android-header.md }}


## iOS XCUI Driver notes
{{#include ../shared/ios-header.md }}