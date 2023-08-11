# Locale: Real Devices
Note: [dependent apps inherit](https://docs.saucelabs.com/dev/test-configuration-options/#appiumotherapps:~:text=Dependent%20apps%20inherit%20the%20configuration%20of%20the%20main%20app%20under%20test) the current setting for the main app. 

If your app's language is tied to locale see the [Setting the Language via Sauce Labs](./language-rdc.md#setting-the-language) section. Otherwise defer to your app's way of picking up Locale, is it a Debug menu item? Are there different builds per region? Will the OS settings matter?

Users can modify some OS Settings during a session but in general you should presume most Settings will be off limits for Public devices. [Private Devices](https://docs.saucelabs.com/mobile-apps/supported-devices/#private-device-cloud) should allow you to change settings at will. If you must change settings Permanently, speak to your Customer Success Manager or open a ticket at support@saucelabs.com. If you must change the settings during a session defer to your Appium Driver or the Sauce Labs Desired Capability options ak [Test Configuration Options](https://docs.saucelabs.com/dev/test-configuration-options/).

## Android UIAutomator 2 Driver Notes
{{ #include ../shared/android-header.md }}

## iOS
{{ #include ../shared/ios-header.md }}
