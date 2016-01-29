# jcadf

jCADF is the Java version of the CADF specification. It provides primitives that will allow you to persist CADF events to disk or collaborate with different components that have to produce or consume them. Currently, events can be logged either in CSV or JSON formats. The accompanying AuditMiddleware class provides helper methods to create events, and log them using the appropriate formats.

Several junit test cases provide instructive samples to show how to use the jCADF methods to create events and log them in one of the supported formats. To get a good view at the mechanism that unveils the use of the CADF event in the context of Java, you will want to take a look at :

•	com.ibm.cadf.middleware.AuditMiddlewareTest
•	com.ibm.cadf.auditlogger.CSVAuditLoggerTest
•	com.ibm.cadf.auditlogger.JsonAuditLoggerTest

The following  is sample log data for CADF events in both CSV and JSON formats :

CSV Format

Id,Timestamp,Action,Observer,Initiator,Target,Outcome,<Measurements>
8f2b7dcf-7a3c-42d9-b378-bfb4dbebeafb,2016-01-29T09:57:36.371 UTC,Send File,Management Component,AuditLoggerTest,Configuration Component,successful,<99e59663-1a11-474a-ac0f-d7c777441090 - MB FileData : 99e59663-1a11-474a-ac0f-d7c777441090 - MB FileData : >

JSON Format

{"typeURI":"http://schemas.dmtf.org/cloud/audit/1.0/event","eventType":"activity","id":"465f2085-2c00-45e7-974e-4f80d56f28ac","eventTime":"2016-01-27T05:23:34.757 UTC","action":"backup/migrate","outcome":"success","initiator":{"id":"44fe680e-c490-4985-bf25-848ea62025b9","typeURI":"data/security/account/admin","name":"root","host":{"address":"9.114.98.227"}},"target":{"id":"45c78e53-4941-4647-b079-6740cf662c44","typeURI":"service/storage/object","name":"s3"},"observer":{"id":"75e983eb-4383-4775-b8f5-031a1bb8bd5b","typeURI":"service/storage/object","name":"gpfs/mcstore"},"measurements":[{"result":"1","metric":{"metricId":"95cee9c1-2c02-41d1-9b2f-7e734ad908db","unit":"file","name":"The number of files that are successfully migrated"}},{"result":"41","metric":{"metricId":"bfeaf175-e6f3-4d66-95b8-6a2dcfc46a30","unit":"byte","name":"File size in bytes"}}],"attachments":[{"content":"accountname=ramcloud","name":"cloudName","contentType":"text"}]}


The best way to see these methods in action is to either fork the project, or download the project's zip file, import the project into eclipse and run or debug the classes listed above. You can then set breakpoints into any area of interest, and consult the log files being created.