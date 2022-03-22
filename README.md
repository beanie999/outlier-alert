# Example New Relic Outlier Alert using Synthetics
This project provides an example New Relic outlier alert using a synthetic Scripted API script. The example looks for the response time in a cluster and fails when any host is suffering from response times greater than 2 standard deviations from the cluster average.

## How it works
The monitor should run on a regular basis (say every minute), testing the response times in the cluster. When an outlier is found the monitor fails and an alert can then be used to send a notification.


## Setup
- Make sure you have a USER key and your account id, then create an Endpoint availability, Scripted API monitor (probably set to run once a minute). 
- Paste in the outlier-alert.js JavaScript code.
- Ensure the USER key and account id are set correctly, the example uses 2 secure credentials (`MIKE_ACCOUNT_ID` and `MIKE_USER_KEY`). Rename these or hardcode them, as appropriate.
- Change the NRQL accordingly (`NRQL_TranCount` variable), for example appName in the WHERE clause and time period (5 minutes will allow for some smoothing of data and reduce the likelihood of false alerts). Note, if you change any of the field names then you will need to reflect this in the JavaScript code.
- Optional - Change the `threshold` variable depending on your needs (the example uses 2 times the standard deviation of the cluster as a whole).
- Optional - Change the `MinTranCount` value, this is the minimum number of transactions a host needs to be executing before it can be considered as an outlier. This is to stop false alerts when transaction numbers are low.
- Test the monitor and set it running.
- Create an alert to watch for this specific monitor. It will alert you when the monitor fails and you can then drill into the monitor failure to see the details.

## Availability
You can safely run the synthetic script from multiple locations.
