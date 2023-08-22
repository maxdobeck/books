# Virtual Devices on Sauce Labs
{{ #include ../shared/appium-header.md }}

Be aware of [your App's requirements](../intro/locale-and-language.md#app-requirements), you may be forced to use real devices. Or vice versa.

Locale and Language are usually tied together. But proceed according to your chosen driver's documentation.

Please note that many commands and capabilities are iOS SIMULATOR only. Or are for Android EMULATORS only. These typically cannot work on Real Devices and will also sometimes require a full simulator/emulator reboot. Or they must be set at runtime, when the virtual device launches.  For example the Execute Method `configureLocalization`: <https://appium.github.io/appium-xcuitest-driver/4.33/execute-methods/#mobile-configurelocalization>


### Appium
#### Android
Some capabilities must be used simultaneously, read the documentation carefully. Like the [locale methods](https://github.com/appium/appium-uiautomator2-driver#app-localization) `appium:locale` & `appium:language`. 
#### iOS
Rely on the XCUI Driver capabilities. Read the [driver documentation and capability list](#ios-xcui-driver-notes).
Caps like [`appium:locale`](https://appium.github.io/appium-xcuitest-driver/4.16/capabilities/) are specifically for Simulators _"If a test is executed on a Simulator then UI locale is changed as well. You can also change Simulator locale in runtime using mobile: configureLocalization extension."_  


## Android UIAutomator 2 Driver Notes
{{ #include ../shared/android-header.md }}


## iOS XCUI Driver notes
{{ #include ../shared/ios-header.md }}