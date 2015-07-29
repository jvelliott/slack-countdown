Countdown program to Slack hook
-------------------------------
Recieve notifications daily about an incoming deadline.

## Setup

There are two ways of setting up. One is to clone this repositry and make any optional modifications to the coundown.py file and deploy it youself to Heroku. The other is to follow
the simple steps below which uses the Heroku button to deploy the app. A prequisite is that 
you have a Heroku app and have added a method of payment on their. Including add ons, even 
though the Heroku Scheduler is free, requires that the account has a method of payment.

1. Create a <a href="https://slack.com/services/new/incoming-webhook" target="_blank"> new incoming webhook</a> for your Slack channel and copy the unique URL. This is the URL countdown.py will be sending post requests to.

1. Press this button to create a new Heroku app:

    <a href="https://heroku.com/deploy" target="_blank">
        <img src="https://www.herokucdn.com/deploy/button.png" alt="Deploy">
    </a>

1. Paste the unique URL into the 'SLACK_URL' field and deploy the app.

1. After deployment, click manage apps. You should also get a message to your Slack channel
	to confirm connection.

1. Click on the Heroku Scheduler, this will open up a dashboard where we can run scripts periodically.

1. We will need run the countdown.py deadline task
The method takes these 2 optional arguments:
```
$ ./countdown  --help
Usage: countdown [options]

Options:
  -d DEADLINE, --deadline=DEADLINE
                        Specify the deadline in ISO format: yyyy-mm-dd
  -e EVENT, --event=EVENT
                        Name of the deadline event
```
i.e.
If the date today is the 16th July 2015 then
- `countdown -d 2015-07-18` should print out “2 days until 18 July 2015”
- `countdown -d 2015-07-18 -e weekend` should print out “2 days until weekend”.

If no argument is given, the default is for the method to post how many days till the
next Christmas.

1. In the terminal type:
	```
	python countdown.py deadline
	```
	followed by your desired arguments.

1. Next specify how often you want the script to run, i.e. how often you want a reminder of your deadline in the Slack Channel.

1. Once this is saved the app is complete.