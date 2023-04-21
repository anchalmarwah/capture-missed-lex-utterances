# capture-missed-lex-utterances/amazon connect
# SUMMARY:

This Solution uses the Event Bridge Rule alongside with "Lambda A" as a Target and a CRON Schedule to run every 14 days. When triggered, "Lambda A" accesses Amazon Lex and retrieves all missed utterances from the past 14 days, along with their respective counts. The details are then written to a CSV file and uploaded to an S3 bucket by "Lambda A".
"Lambda B" is set up to poll the S3 bucket and is triggered by the S3PutObject API in a specific bucket folder. 
Once triggered, "Lambda B" sends an email via SES to the end user with the attached CSV file. The CSV file contains a summary of the missed utterances in "Key": "Value" format, where "Missed Utterances" is the key and "Count" is the value.
This allows the end user to retrieve the attached CSV file in a general summary format and view all missed utterances along with their respective counts, providing them with valuable information that can be used to improve their interactions with the bot.
