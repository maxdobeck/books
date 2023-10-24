# Locale, Language, & Location Testing

## Abstract
You may need to test behaviors related to time & space. Someone flying from Tokyo to Hawaii should have the same user experience as someone flying from London to Chicago. Their day or their job or their life should not be interrupted because the timestamp is wrong and their app cannot handle a transaction. 

Frustrating user experiences will drive users away. Quickly. Product Quality can't be sacrificed for speed of delivery but neither can speed slow down in the name of quality. Security patches must be applied, new features must be built, the world turns.

## Execution
Testing using a framework like XCUI test, Playwright, or Appium can be painful or impossible when APIs are not available. Especially in the mobile space where automating the Settings on various device models is a time sink all on its own. Simply asserting the region is correct or setting a timezone may take several attempts and require endless exception handling. 

As a litmus test, there should be an API or method builtin to handle your use case. If you MUST automate individual setup steps then you need to discard the test and move lower on [the testing pyramid](https://martinfowler.com/articles/practical-test-pyramid.html).

## Conclusion
### Time
* Do not test timezone or temporal behaviors with End to End tests, or with tools like Playwright, Appium, or Selenium.
* Do test using Unit tests and integration tests at the API or backend layer. 
* Do mock the UI and views so that these can be quickly tested without worrying about the underlying Operating System.
* Do write short fast tests that can run dozens or hundreds of times a day.

### Locale
* Do test Locale behaviors in an End-to-End style manner.

Testing integrated systems is usually easy with any testing Framework. Like: asserting Third Party Ads are localized inside your App or Site.  This is achievable with mocking of IP locations using WonderProxy and/or Sauce Connect.

Setting the Locale is fully supported on iOS and Android.

### Language
* Do test accuracy of translations.
* Do test the UI/layout is not impacted by language changes.
* Do test that the language is correct for the region/user.

Setting the Language is fully supported on iOS & Android.

Localizing your product is a common procedure in the software lifecycle. There's support, tools, and common workflows. Not much is unsupported here.

# App Requirements
Things you may need to know, or may be asked by Sauce Labs employees.
1. How does you application determine geo-location? What third party packages and APIs are used?
2. Are all third party packages up-to-date?
3. Is your application [Obfuscated](https://promon.co/security-news/code-obfuscation/)? 
4. Is your application hardened by a third party or Standard Library tool like Promon or [ProGuard/R8 compiler](https://developer.android.com/build/shrink-code#:~:text=Instead%2C%20the%20plugin%20works%20with%20the%20R8%20compiler%20to%20handle%20the%20following%20compile%2Dtime%20tasks%3A)?

For example, you may need to test how an app or third party code behaves in a specific geolocation. If your app detects location using IP address approximation you can easily & reliably automate this with [WonderProxy](https://docs.saucelabs.com/basics/integrations/wonderproxy/#overview). This is an important distinction because changing the locale won't have an impact if IP geolocation/approximation is used. 

NOTE: your experience and options will vary greatly depending on your platform. If you test on Virtual Devices you'll have different tools compared to Real Devices. Likewise your options and expected behaviors could change when comparing iOS vs Android. 

# What is being tested?
- Temporal behavior
- Location(fine, geographically)
- Location(broad, what country is user in?)
- UI layout & rendering that use time on one graph axis. Or a table that has a column for time.
- UX Triggering promotions and other behavior based on time of day or day or day of week. Maybe push notifications at specific times? 


## Further reading 
>XCUI (iOS) Driver documentation -> <https://appium.github.io/appium-xcuitest-driver/4.16/>
>
>UIAutomator2(Android) Driver Documentation -> <https://github.com/appium/appium-uiautomator2-driver#readme>