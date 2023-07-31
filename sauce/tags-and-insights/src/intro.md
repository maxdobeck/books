# Introduction. Leveraging Sauce Labs Through Metadata 

## Getting Started
Get a copy-paste ready-to-go Desired Capability sample from Sauce Labs' [Platform Configurator](https://saucelabs.com/products/platform-configurator#/). For details on Tags & Builds check the [Builds, Tags, and Names walkthrough in the docs](https://docs.saucelabs.com/basics/test-config-annotation/test-annotation/#use-build-ids-tags-and-names-to-identify-your-tests).


## Details
Sauce Labs exists as a platform, and for many users app.saucelabs.com is a website only used frequented while debugging. The typical draw is assets like Screenshots, Videos, or Device logs. However this is only the tip of the iceberg, Sauce Labs offers the ability to categorize and groups tests by whatever paradigm you or your teams use.

If you run Builds or Specs and would like each instance of these grouped visually and logically in Sauce Labs you can do it!

Then all users can consume the über grouping in the <https://app.saucelabs.com> UI or via our [REST API](https://docs.saucelabs.com/dev/api/) or [Webhooks](https://docs.saucelabs.com/basics/integrations/webhooks/).


## Example
This is an arbitrary example in python, with your given framework, like [WDIO](https://webdriver.io/) you may need to take a wholly different approach. In this example the key highlights are the `sauce_options` object. In any language or any framework you will most likely have this decoupled, or operating on environment variables. 

In this example I'm debugging something from a work laptop, not a CICD pipeline. Once I'm done with my debugging I could instead fetch the `name` and `build` from an environment variable unique to the pipeline. Or I could set my own variable now, locally, and it could read "John's Laptop" or "Sarah's Laptop". This is helpful because:

1. at a glance you'll know whether you should be interested in a set of results
2. the build string becomes a hyperlink in the Sauce Labs UI and you can then see all associated tests

Optionally I could [add tags](https://docs.saucelabs.com/dev/test-configuration-options/#tags) instead of or in addition to a build name. In fact you may want to focus on tags since they're an array of strings. That means all of your tests could have slightly different Tags!

```python
# python code example 
VERSIONS = ['15.2', '14.3', '12.2', '12.0']

sauce_options = {
    'appiumVersion': '2.0.0',
    'build': 'ad hoc from laptop',
    'name': 'timing test'
}

ios_caps = {
    'appium:deviceName': "iphone simulator",
    'browserName': "safari",
    'appium:platformVersion': random.choice(VERSIONS),
    'platformName': "iOS",
    'appium:automationName': "XCUITest",
    'sauce:options': sauce_options
}

android_caps = {
    'appium:deviceName': "Android GoogleAPI Emulator",
    'browserName': "chrome",
    'appium:platformVersion': "13.0",
    'platformName': "Android",
    'appium:automationName': "UiAutomator2",
    'sauce:options': sauce_options
}
```

Whether you keep the sauce:options details inline, or as a shared global object is down to your use case. And it may differ from test-to-test!  But keep in mind you can overwrite some of these objects with Annotations.

### Annotations
<https://docs.saucelabs.com/basics/test-config-annotation/test-annotation/>
NOTE: You'll need to use the JavaScript Executor in your framework/language of choice.

Annotations can be used just like Build & Name. But this lets you overwrite settings _during_ test execution. Say for example if you end up going down the sad path of code execution, maybe an element is not loading and can't be found `:/` .  Just add an Annotation via the `JavaScriptExecutor` and add in any details you need.

Read more from an Appium Perspective here: <https://appium.io/docs/en/2.0/guides/execute-methods/>. 

### REST API - Jobs
<https://docs.saucelabs.com/dev/api/jobs/#update-a-job>

Many of the same use cases apply retroactively, after the job has finished. Keep in mind this overwrites and does not append to existing data. 

You may need to do this ad hoc out of necessity or you may just setup your CICD pipeline this way.