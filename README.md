# Sending SMS With Python

In this tutorial, you will use the Python module SinchSMS to [send an SMS message with Sinch](https://www.sinch.com/products/sms-api/ "SMS"). With the Sinch SMS API, you can build anything from a simple notification service to [two-factor authentication](https://www.sinch.com/features/sms-features/two-factor-authentication/ "Two Factor Authentication") solutions.

## Video

We have also turned this tutorial into a quick video walkthrough. Click on the image below to watch the tutorial.

<a href="http://www.youtube.com/watch?feature=player_embedded&v=dE-xyeBNAvs" target="_blank"><img src="/images/sending-sms-python.jpg" 
alt="Send SMS in Python" width="400" height="281" border="10" /></a>

For SMS pricing by destination, visit our [pricing pages](https://www.sinch.com/pricing/sms-prices/ "SMS Prices").

## Setup

1.  Create a [Sinch developer account](www.sinch.com/signup)
2.  In your developer dashboard, click “Apps” in the left-hand menu
3.  Click “Create new app”
4.  Name your app and click “Create”
5.  Take note of your app key and secret, you will need them in a few minutes
6.  Install the module using `pip install sinchsms`

## Sending an SMS via the API

Launch the interactive console by typing `python` in your command line and type the below:

```py
import time
from sinchsms import SinchSMS

number = '+yourmobilenumber'
message = 'I love SMS!'

client = SinchSMS(your_app_key, your_app_secret)

print("Sending '%s' to %s" % (message, number))
response = client.send_message(number, message)
message_id = response['messageId']

response = client.check_status(message_id)
while response['status'] != 'Successful':
    print(response['status'])
    time.sleep(1)
response = client.check_status(message_id)
print(response['status'])
```

If you don't want to use a module, you can find the source code for the module on GitHub: [https://github.com/sinch/python-sinch-sms](https://github.com/sinch/python-sinch-sms)

### What's next?

In the coming months, we will start supporting incoming SMS and have a packaged solution for verifying phone numbers through SMS and calling. Stay tuned.

Happy SMSing!

-[Christian](https://www.sinch.com/author/christian/)
