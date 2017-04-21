Forked version of the original [grading-assigner](https://github.com/udacity/grading-assigner) with support for push notifications on an [Android App](https://github.com/kartikarora/udacity-reviewer-android/releases/latest).

> The app only works if grading assigner is run with an `FCM_TOKEN` using this fork.

> Also, the app must be run at least once before running the script to complete registration. The `FCM_TOKEN` is generated in the app.

# Usage

Requires the `requests` module, which you can either install globally or in a virtualenv.

Install: pip install -r requirements.txt (expects Python to be installed along with pip)

```
usage: grading-assigner.py [-h] [--auth-token TOKEN]

Poll the Udacity reviews API to claim projects to review.

optional arguments:
  -h, --help            show this help message and exit
  --auth-token TOKEN, -T TOKEN
                        Your Udacity auth token. To obtain, login to
                        review.udacity.com, open the Javascript console, and
                        copy the output of
                        `JSON.parse(localStorage.currentUser).token`. This can
                        also be stored in the environment variable
                        UDACITY_AUTH_TOKEN.
  --debug, -d           Turn on debug statements.
  --fcm-token TOKEN, -F TOKEN
                        Your FCM Token(s). Available under preferences in the
                        app. Add each token after a whitespace
```

# Example
```
$ ./grading-assigner.py --auth-token <YOUR_UDACITY_REVIEW_API_TOKE> --fcm-token <YOUR_FCM_TOKEN_COPIED_FROM_PHONE_1> <YOUR_FCM_TOKEN_COPIED_FROM_PHONE_2>
|2016-08-03 19:28:43,288| FCM Token found, Push Initialized
|2016-08-03 19:28:43,456| Number of devices: 2
|2016-08-03 19:28:44,766| Requesting certifications...
|2016-08-03 19:28:45,357| Found certifications for project IDs: [2, 3] in languages [u'pt', u'en']
|2016-08-03 19:28:45,358| Polling for new submissions...
|2016-08-03 19:28:45,358| Will poll for projects/languages [{'project_id': 2,
'language': u'pt'}, {'project_id': 2, 'language': u'en'}, {'project_id': 3,
'language': u'pt'}, {'project_id': 3, 'language': u'en'}]
|2016-08-03 19:28:45,751| Creating a request for 2 project(s) in 2 languages
|2016-08-03 19:28:47,876|
|2016-08-03 19:28:47,876| =================================================
|2016-08-03 19:28:47,876| You have been assigned to grade a new submission!
|2016-08-03 19:28:47,876| View it here: https://review.udacity.com/#!/submissions/237
|2016-08-03 19:28:47,876| =================================================
|2016-08-03 19:28:47,876| Continuing to poll...
|2016-08-03 19:28:48,042| Creating a request for 2 project(s) in 2 languages
|2016-08-03 19:28:50,177|
|2016-08-03 19:28:50,178| =================================================
|2016-08-03 19:28:50,178| You have been assigned to grade a new submission!
|2016-08-03 19:28:50,178| View it here: https://review.udacity.com/#!/submissions/238
|2016-08-03 19:28:50,178| =================================================
|2016-08-03 19:28:50,178| Continuing to poll...
|2016-08-03 19:28:50,353| Waiting for assigned submissions < 2
|2016-08-03 19:28:55,531| Waiting for assigned submissions < 2
^C|2016-08-03 19:28:56,591| Cleaning up active request
```

Press ctrl-c to quit.
