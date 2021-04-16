### SLT setup using LTRC in S4 and load data from SAP Data Intelligence pipelines


#### Prepare connections and security in ABAP system

See SAP Note: [2831756 - SAP Data Hub/ Data Intelligence ABAP Integration - Security Settings](https://launchpad.support.sap.com/#/notes/2831756)  
The access to ABAP operators (standard and custom), ABAP meta data or data stored in tables, views, CDS views, ODP (availability depending on the connected backend) or others is protected by a whitelisting and authorization concept for security reasons.

If the whitelisting is not maintained properly, or the authorizations are not assigned, the respective request from SAP Data Intelligence to the ABAP-based remote system will fail.

In particular, you would face the following issues:
* You cannot use your ABAP operators within SAP Data Intelligence.
* You cannot browse ABAP meta data.
* You cannot preview ABAP data.

Follow the steps in this excellent blog [How To Integrate SAP Data Intelligence and SAP S/4HANA AnyPremise](https://blogs.sap.com/2020/05/27/how-to-integrate-sap-data-intelligence-and-sap-s-4hana-anypremise/)  



#### Prepare the source system (ABAP system)
First of all we will logon to the SAP Business Suite system to prepare SLT. Before we can communicate from our SAP Data Hub pipeline with SLT, we need to have a SLT Configuration in place (which you can imagine like a project entity inside SLT, representing basically a combination of a source system connection and a target system connection).

1. Therefore go to the SLT cockpit by entering transaction code **ltrc** in the command field. Within this environment you can find details to existing SLT data replications and you can also create, monitor and execute additional ones.
1. Click on “new” to create a new SLT Configuration.  
  ![](/SLT/img/2_createSltConfig.png)
1. Provide a SLT Configuration Name, for instance “SLT_DEMO” and click “next”.  
  ![](/SLT/img/3_nameConfig.png)
1. Specify the source system connection, in our case RFC Connection equals none (as we like to load data out of the same system, that also SLT is running on). Click "next".  
  ![](/SLT/img/4_specifySourceConnection.png)
1. Specify the target system connection to SAP Data Hub or SAP Data Intelligence. Therefore choose option “Others” and specify “SAP Data Hub / SAP Data Intelligence”.  
  ![](/SLT/img/5_specify_target.png)
1. Define the SLT Job Settings. If you plan just a simple test of replicating a single table to SAP Data Hub, it is fine to provide one job for “Data Transfer Jobs” and as well for “Calculation Jobs”.  
  ![](/SLT/img/6_JobSettings.png)
1. Click “next” and then “create”.  

Note down the **Mass Transfer ID**, that has been generated. This **ID** uniquely identifies the SLT Configuration and is required later for the configuration of the SLT Connector operator.



