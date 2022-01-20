# Directory Proxy Server Log Source

### Set-Up Process for Log Source

1. Go to Log Analytics —> Administration Home —> click the gear in the top right corner —> Import Configuration Content —> upload the attached file

2. If you expand the zip file and look at the README, you can see the log source, log parser, custom fields, and standard fields used 

3. Open the Log Source and set the File Name Pattern to the file path that points to your access logs

### Connect Directory Proxy Server to Log Source

1. Deploy Cloud Agent on Directory Proxy Server (https://docs.oracle.com/en/cloud/paas/management-cloud/emaig/install-cloud-agents.html)

2. License the Host that DPS is running on (https://docs.oracle.com/en/cloud/paas/management-cloud/omcgs/oracle-management-cloud-license-information.html#GUID-566DE2D1-C321-4AEB-9A34-07C3156D0975)

3. Associate Entity to Log Source (https://docs.oracle.com/en/cloud/paas/management-cloud/logcs/manage-existing-target-associations.html#GUID-1393A424-85EA-4C3F-AC80-637A7861C1E6)

4. If the entity isn’t popping up, the type on the log source may be incorrect (Right now it’s set up to be a Linux Host). Create a copy of the log source and change entity type to whatever matches the DPS entity. 


Content
Sources: [Directory Proxy Server Access Logs V3]
Parsers: [Directory Proxy Server Access Log Format]
Fields: [DPS Bind DN, DPS Client Port, DPS Connection Handler, DPS Message, DPS Operation Number, DPS Search Attributes, DPS Search Base, DPS Search Filter, DPS Server Port, DPS nentries, DPS s_conn, DPS s_msgid]

Reference
Fields: [cat, cid, clnthostip, elaptimereal, errid, mbody, msg, msgid, oper, prot, reas, sevlvl, srvrhostname]


Note: This log source should be considered more of a sample or skeleton log source, since it is not technically considered fully production ready. For example, it may not cover every log pattern since we were working off a subset of data or may reference fields you would prefer not to use.

Base Log Parser: Directory Proxy Server Access Log Format
Log Source: Directory Proxy Server Access Logs
Custom Fields:
-	DPS Message (base parser)
-	DPS Connection Handler (profile)
-	DPS Operation Number (operation)
-	DPS Operation Body
-	DPS nentries (operation) 
-	DPS s_msgid
-	DPS s_conn
