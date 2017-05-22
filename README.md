# gurgle
Provides for the flow of Elite:Dangerous faction influence data from providers (EDDN, Journal Log) to Google Sheets.

The sheet.js provides a simple web app for Google Sheets that accepts incoming data (POST or GET) and updates the specified sheet with any values that match the column titles (row 1). This can be simply configured through the Script Editor using the Publish -> Deploy as web app... option.

The eddn.py provides for listening to the Elite Dangerous Data Network which provides a ZeroMQ (0MQ) feed of events supplied through various client applications. We specifically listen for the FSDJump events that detail the faction influences in any visited system, parse the JSON to create data that we can then POST to the Google Sheet web app.

The file.py provides an equivalent that simply takes a Journal log file as the first argument and consumes the FSDJump events in the same way.

## TODO
 - Authentication (using simple API application key).
 - Improve resilience of the POST to Google Sheets, which can sometimes fail and should be retried at least once.
 - Improve logging capabilities.
 - PowerShell client implementation that monitors player journals (for those not using EDDN feeder apps).
 - Further refactor, but without sacrificing simplicity.