### Sauce: App Settings
Check your app's [Default Settings](https://docs.saucelabs.com/mobile-apps/live-testing/live-mobile-app-testing/#default-app-settings) like Device Language from the Settings page. 

>To view or change the app settings, on the App Management page, hover over the app and then click Settings.
>![app-settings-screenshot](../images/app-settings.png) 
>These are GLOBAL for all users who can see this app.

Changing the Language Dropdown influences the LOCALE of your app. How your app handles a changing locale is going to depend on the app itself most of the time. This could involve third party code for specific workflows like payments or translating timezones. You may have some [i18n](https://en.wikipedia.org/wiki/Internationalization_and_localization) package that tries to switch to translated versions of the app.
