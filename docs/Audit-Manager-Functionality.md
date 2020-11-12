## Audit Manager

The Audit Manager component receives a request to audit and store data, validates if the request is from an authorized source, securely store the requested data and respond back with an acknowledgment of storage (Success/Failure). 

Upon receiving a request to store audit logs with the input parameters, the audit manager performs the following steps:

1. Validates if all required input parameters have been received as listed below for each specific request
   * Audit Event ID - Mandatory
   * Audit Event name - Mandatory
   * Audit Event Type - Mandatory
   * Action DateTimestamp - Mandatory
   * Host - Name - Mandatory
   * Host - IP - Mandatory
   * Application Id - Mandatory
   * Application Name - Mandatory
   * Session User Id - Mandatory
   * Session User Name - Mandatory
   * Module Name – Optional
   * Module Id - Optional
   * ID - Mandatory
   * ID Type - Mandatory
   * Logged Timestamp - Mandatory
   * Audit Log Description - Optional
   * cr_by, (Actor who has done the event) - Mandatory
   * cr_dtimes, (When this row is inserted into Database) - Mandatory
1. Validates if the Audit Request is not for one of the exempted events as listed in the Exempted Audit Event List/Table
1. Time Stamp (format: yyyy-MM-ddThh:mm:ss) and unique Audit ID are generated by the Audit manager component for each Audit Request
1. All the input parameters received are stored in the audit database
1. Personally Identifiable Information (PII) data as listed below is not stored
   * Name
   * DOB
   * Contact Number
   * Citizenship
   * Legal Status
   * Gender
   * Race/Ethnicity
   * Any Government Identification Number
1. Responds with the acknowledgment to source
   * Success
   * Failure
1. Raises an alert in case of an exception 

The Audit Manager being an asynchronous service, also supports prevention of Audit data loss in cases where Audit service itself is down or the Audit Database is down. Audit Manager does it by putting any storing any audit records which are not stored in DB into a Log file and continuing with capturing Audits.

## Log Manager
Log manager provides following functionalities:

1. Generate logs across the application
1. Store generated logs in configured location
1. Support for reading the logger configurations through as external file
1. Support addition log level to a particular logger dynamically

## List of Configurable Parameters
[**Link to Configurable Parameters of Kernel**](https://github.com/mosip/mosip-config/blob/master/config-templates/kernel-env.properties)

## Kernel API 
[**Refer to Wiki for more details on Kernel API**](Kernel-APIs.md)
