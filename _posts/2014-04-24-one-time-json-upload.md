---
layout: post
title: One-Time JSON Upload
categories: [integrations, json-import]
summary: Import data by uploading a single .json file.
---
* Table of Contents
{:toc}
* * *

This guide explains how to import data from individual .json files.

## 1. Navigate to the Upload Area

The [JSON upload area][json-new] is located under your site's External Data Sources. You can reach it by doing the following:

* Go to [*Settings*][1] (the small gear tab)
* Click [*Data Integrations*][2]
* Click *Add Data from JSON File*

![JSON Upload Step 1][screenshot-1]

## 2. Select your JSON file

* Select "Upload JSON File" as the Import Option.
* Locate the file to upload on your computer.

Please refer to our [reference for details on how to format your JSON file][file-format].

## 3. Preview the results

If your file is formatted correctly, we'll show you a preview of the events and properties to be imported.

![JSON Upload Step 2][screenshot-2]

## 4. Complete the Upload

Once everything looks good, confirm the upload. Just as with any other data source that is bringing in events and properties, please wait **2-5 hours** for the data to become available in your reports.

## 5. Check the Status

Completed uploads will be archived, and you will be able to refer to when they were originally imported.

For the purpose of housekeeping, you can delete completed entries. Note that **this does not delete the events that were brought in from the JSON file.**

[1]: https://app.kissmetrics.com/settings
[2]: https://www.kissmetric.com/external_data
[json-new]: https://app.kissmetrics.com/external_data/json.new
[file-format]: /integrations/json-import

[screenshot-1]: http://kissmetrics-support-files.s3.amazonaws.com/assets/integrations/json-import/json-linking-step-5.png
[screenshot-2]: http://kissmetrics-support-files.s3.amazonaws.com/assets/integrations/json-import/json-import-preview.png
