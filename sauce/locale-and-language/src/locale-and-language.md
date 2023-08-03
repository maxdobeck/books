# Locale & Language Testing
### Pre-Requisites
Things you may need to know to effectively test or may be asked by Sauce Labs.
1. How does you application determine geo-location? What third party packages and APIs are used?
2. Are all third party packages up-to-date?
3. Is your Application [Obfuscated](https://promon.co/security-news/code-obfuscation/)? 
4. 

For example, you may need to test how an app or third party code behaves in a specific geo-location. If your app detects location using IP address approximation you can easily & reliably automate this with [WonderProxy](https://docs.saucelabs.com/basics/integrations/wonderproxy/#overview).

NOTE: your experience and options will vary greatly depending on your platform. If you test on Virtual Devices you'll have different tools compared to Real Devices. Likewise your options and expected behaviors could change when comparing iOS vs Android. 

## What is being tested?
Temporal
Location(geographically, fine grained)
Location(broad, what country is user in?)
