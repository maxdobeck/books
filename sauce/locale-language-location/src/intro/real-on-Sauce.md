# Real Devices on Sauce Labs
{{ #include ../shared/appium-header.md }}

{{ #include ../shared/sauce-app-settings.md }}

### Appium
#### iOS 
Its important to be aware of what the Appium server can and can't do. For example [`appium:locale`](https://appium.github.io/appium-xcuitest-driver/4.16/capabilities/) is specifically for Simulators _"If a test is executed on a Simulator then UI locale is changed as well. You can also change Simulator locale in runtime using mobile: configureLocalization extension."_ If you're testing on Real Devices exclusively or with Espresso/XCUI tests you won't have access to that Appium Capability. 

#### Android
Contradictory to the iOS example Android can use Appium 2.0 to test Locale/Language. Consult the documentation <https://github.com/appium/appium-uiautomator2-driver#app-localization>. In this case the 

## Android UIAutomator 2 Driver Notes

{{ #include ../shared/android-header.md}}

You CAN test with Appium + Real Devices. But you can also rely on the Language dropdown found in the App Settings. 

## iOS
{{ #include ../shared/ios-header.md}}

Rely on the [Sauce Labs App Settings](#sauce-app-settings) for Real Device tests.
