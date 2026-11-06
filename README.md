# Data Dispatch

Sends the rows of a CSV, Excel or JSON file to a Google Apps Script endpoint, one request per row.

## What it does

- Reads `.csv`, `.xlsx`, `.xls` and `.json` files, and queues several files at once. For a workbook with more than one sheet, a picker chooses which sheets to send.
- Checks that every row has all 26 required fields: `date`, `year`, `class`, `month`, `region`, `pharmacy`, `totalPrescription`, `insuranceCoveredPrescription` and 18 category columns named in Arabic. Header names are case-sensitive and their order does not matter.
- Sends rows one at a time, with a delay of 800 ms between requests, and shows progress and a result for each row.
- Downloads a blank template as CSV or JSON.
- Switches between system, light and dark themes.

## What it does not do

- It does not retry failed rows.
- It treats a row as sent only when the response text contains "success". It has no authentication of its own.
- The field list and the endpoint address are fixed in `index.html`. It cannot map other column names.
- It stores only the theme choice (`dispatchThemeMode`) in `localStorage`.

## Network and install

Calls a Google Apps Script web app with one GET request per row, passing the row as a query parameter, and loads SheetJS 0.18.5 from cdnjs. It makes no other requests. Not installable; no service worker.

## Built with

One HTML file, with no build step and no framework. SheetJS 0.18.5 reads Excel files.

## Run locally

Serve the folder with any static file server. Sending needs a connection to the endpoint.
