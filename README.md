# Salesforce Bulk API

## Which API Should I Use?
* [Salesforce APIs](https://help.salesforce.com/articleView?id=integrate_what_is_api.htm&language=en_US&type=0)

## When to use Bulk API
* Bulk API is based on REST principles and is optimized for loading or deleting large sets of data. You can use it to query, queryAll, insert, update, upsert, or delete many records asynchronously by submitting batches. Salesforce processes batches in the background.
* SOAP API, in contrast, is optimized for real-time client applications that update a few records at a time. You can use SOAP API for processing many records, but when the data sets contain hundreds of thousands of records, SOAP API is less practical. Bulk API is designed to make it simple to process data from a few thousand to millions of records.
* The easiest way to use Bulk API is to enable it for processing records in Data Loader using CSV files. Using Data Loader avoids the need to write your own client application.

## What can you do with the Bulk API?
* The REST Bulk API lets you query, queryAll, insert, update, upsert, or delete a large number of records asynchronously. The records can include binary attachments, such as Attachment objects or Salesforce CRM Content. You first send a number of batches to the server using an HTTP POST call and then the server processes the batches in the background. While batches are being processed, you can track progress by checking the status of the job using an HTTP GET call. All operations use HTTP GET or POST methods to send and receive CSV, XML, or JSON data.
