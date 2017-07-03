# Salesforce Bulk API

## Which API Should I Use?
* [Salesforce APIs](https://help.salesforce.com/articleView?id=integrate_what_is_api.htm&language=en_US&type=0)

## When to use Bulk API
* Bulk API is based on REST principles and is optimized for loading or deleting large sets of data. You can use it to query, queryAll, insert, update, upsert, or delete many records asynchronously by submitting batches. Salesforce processes batches in the background.
* SOAP API, in contrast, is optimized for real-time client applications that update a few records at a time. You can use SOAP API for processing many records, but when the data sets contain hundreds of thousands of records, SOAP API is less practical. Bulk API is designed to make it simple to process data from a few thousand to millions of records.
* The easiest way to use Bulk API is to enable it for processing records in Data Loader using CSV files. Using Data Loader avoids the need to write your own client application.

## What can you do with the Bulk API?
* The REST Bulk API lets you query, queryAll, insert, update, upsert, or delete a large number of records asynchronously. The records can include binary attachments, such as Attachment objects or Salesforce CRM Content. You first send a number of batches to the server using an HTTP POST call and then the server processes the batches in the background. While batches are being processed, you can track progress by checking the status of the job using an HTTP GET call. All operations use HTTP GET or POST methods to send and receive CSV, XML, or JSON data.

## How Bulk API works?
* You process a set of records by creating a job that contains one or more batches. The job specifies which object is being processed and what type of action is being used (query, queryAll, insert, upsert, update, or delete). A batch is a set of records sent to the server in an HTTP POST request. Each batch is processed independently by the server, not necessarily in the order it is received. Batches may be processed in parallel. It's up to the client to decide how to divide the entire data set into a suitable number of batches.
* A job is represented by the JobInfo resource. This resource is used to create a new job, get status for an existing job, and change status for a job. A batch is created by submitting a CSV, XML, or JSON representation of a set of records and any references to binary attachments in an HTTP POST request. When created, the status of a batch is represented by a BatchInfo resource. When a batch is complete, the result for each record is available in a result set resource.
* Processing data typically consists of the following steps:
1. Create a new job that specifies the object and action.
2. Send data to the server in a number of batches.
3. Once all data has been submitted, close the job. Once closed, no more batches can be sent as part of the job.
4. Check status of all batches at a reasonable interval. Each status check returns the state of each batch.
5. When all batches have either completed or failed, retrieve the result for each batch.
6. Match the result sets with the original data set to determine which records failed and succeeded, and take appropriate action.

* At any point in this process, you can abort the job. Aborting a job has the effect of preventing any unprocessed batches from being processed. It doesn't undo the effects of batches already processed.

## CORS (Cross-origin resource sharing)
* CORS is a W3C recommendation that enables web browsers to request resources from origins other than their own (cross-origin request). For example, using CORS, a JavaScript script at https://www.example.com could request a resource from https://www.salesforce.com.

## Sending HTTP request with cURL
