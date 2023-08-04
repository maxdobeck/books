# Locale & Language Testing
### Pre-Requisites
Things you may need to know to effectively test or may be asked by Sauce Labs.
1. How does you application determine geo-location? What third party packages and APIs are used?
2. Are all third party packages up-to-date?
3. Is your application [Obfuscated](https://promon.co/security-news/code-obfuscation/)? 
4. Is your application hardened by a third party or stdlib tool like Promon or [ProGuard/R8 compiler](https://developer.android.com/build/shrink-code#:~:text=Instead%2C%20the%20plugin%20works%20with%20the%20R8%20compiler%20to%20handle%20the%20following%20compile%2Dtime%20tasks%3A)?

For example, you may need to test how an app or third party code behaves in a specific geo-location. If your app detects location using IP address approximation you can easily & reliably automate this with [WonderProxy](https://docs.saucelabs.com/basics/integrations/wonderproxy/#overview).

NOTE: your experience and options will vary greatly depending on your platform. If you test on Virtual Devices you'll have different tools compared to Real Devices. Likewise your options and expected behaviors could change when comparing iOS vs Android. 

## What is being tested?
- Temporal behavior
- Location(fine, geographically)
- Location(broad, what country is user in?)
- UI layout & rendering that use time on one graph axis. Or a table that has a column for time.
- UX Triggering promotions and other behavior based on time of day or day or day of week. Maybe push notifications at specific times? 


## Further reading 
>XCUI (iOS) Driver documentation -> <https://appium.github.io/appium-xcuitest-driver/4.16/>
>
>UIAutomator2(Android) Driver Documentation -> <https://github.com/appium/appium-uiautomator2-driver#readme>