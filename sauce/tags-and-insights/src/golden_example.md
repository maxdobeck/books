# Real-ish World Example

```python
# author Max Dobeck
from appium import webdriver
import os
import emoji
import random
import logging
import traceback
from tickets.glue import update_test_name

# optional stuff to help me track details in 
# a debugging session.
# Setting instrumentation settings here programmatically
# also makes things easier.
NAME = "app fails to launch"
TAGS = ['har file', 'not opening', '146006']
# Often need to test in multiple data centers
APPS_EU = ['e97327-1abc-fake']
APPS_US = ['190a32a-2abc-fake',
           '8b02b60-3abc-fake',
           '9b1e1aa-2abc-fake']
APP = random.choice(APPS_EU)
NAME = NAME + " " + APP
DEVICES = "^(iPhone 12.* | iPhone 13.* | iPhone 11.*).*"
logging.getLogger().setLevel(logging.INFO)

desired_capabilities = {}
desired_capabilities['platformName'] = 'ios'
# keeping platformVersion commented out selects ANY OS version
# desired_capabilities['platformVersion'] = '14'
# desired_capabilities['deviceName'] = DEVICES
# Select ANY iPhone device
desired_capabilities['deviceName'] = "iPhone.*"
desired_capabilities['app'] = "storage:" + APP
desired_capabilities['autoAcceptAlerts'] = True
sauce_options = {}
sauce_options['build'] = "<Jira Number> something not working"
sauce_options['tags'] = TAGS
sauce_options['name'] = NAME
desired_capabilities['sauce:options'] = sauce_options


username = os.getenv("SAUCE_USERNAME")
access_key = os.getenv("SAUCE_ACCESS_KEY")
credentials = f'https://{username}:{access_key}@'
ENDPOINT = credentials + 'ondemand.eu-central-1.saucelabs.com:443/wd/hub'

driver = webdriver.Remote(ENDPOINT, desired_capabilities)
stopwatch = emoji.emojize(":stopwatch:")
try:
    logging.info(stopwatch, "test started")
    driver.implicitly_wait(10)
    # this is returned by Sauce Labs to the client and makes 
    # a convenient URL hyperlink available
    # to STDOUT, your logs, or your console 
    job_link = driver.capabilities['testobject_test_report_url']
    logging.info(
        "test started: %s %s",
        emoji.emojize(":mobile_phone_with_arrow:"),
        job_link)

except Exception as e:
    # Uh oh something has gone wrong!
    # Normally you'd see other exception handling blocks for specific Appium
    # or Webdriver Exceptions.
    #
    # In my case I don't care too much what went wrong, I just need 
    # everything logged.
    # 1st I log using traceback.
    logging.error(traceback.format_exc())
    # 2nd we mark the job as failed while running, no need for REST API 
    # housekeeping after
    driver.execute_script('sauce:job-result=failed')
    # Naively spit out the full error to the logging utility
    logging.error(e)
    # Add more context clues for myself and others when looking back at 
    # the job on saucelabs.com
    driver.execute_script(f'sauce:context=err: {str(e)}')
    # Maybe update the test name for sanity
    update_test_name(f"BROKEN: {NAME}")
    # Gracefully close the Sauce Labs session. Otherwise the jobs get 
    # marked as Abandoned or Idled. Then there's a lot of noise from 
    # these Errored jobs.
    driver.quit()
    # For my own sanity I log a emoji to the terminal and a hyperlink 
    # to the job
    logging.error("ERROR: %s %s", emoji.emojize(":cross_mark:"), job_link)
    # Make sure to end the process with non-zero status, ending with a 
    # zero at this moment could have unintended consequences if another 
    # tool wraps your code, or you're in a docker container. 
    exit(1)

# happy path. We gracefully end here if everything goes well
driver.execute_script('sauce:job-result=passed')
driver.quit()
logging.info(emoji.emojize("passing :check_mark_button:"), job_link)
```