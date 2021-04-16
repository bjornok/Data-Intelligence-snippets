### SLT setup using LTRC in S4 and load data from DI pipelines


Using

#### Prepare the source system (ABAP system)
First of all we will logon to the SAP Business Suite system to prepare SLT. Before we can communicate from our SAP Data Hub pipeline with SLT, we need to have a SLT Configuration in place (which you can imagine like a project entity inside SLT, representing basically a combination of a source system connection and a target system connection).

1. Therefore go to the SLT cockpit by entering transaction code **ltrc** in the command field. Within this environment you can find details to existing SLT data replications and you can also create, monitor and execute additional ones.
1. Click on “new” to create a new SLT Configuration.
  ![](/SLT/2_createSltConfig.png)
1. Provide a SLT Configuration Name, for instance “SLT_DEMO” and click “next”.
  ![](/SLT/3_nameConfig.png)
1. Specify the source system connection, in our case RFC Connection equals none (as we like to load data out of the same system, that also SLT is running on). Click "next".        
  ![](/SLT/4_specifySourceConnection.png)
1. Specify the target system connection to SAP Data Hub or SAP Data Intelligence. Therefore choose option “Others” and specify “SAP Data Hub / SAP Data Intelligence”.
  ![](/SLT/5_specify_target.png)
1. Define the SLT Job Settings. If you plan just a simple test of replicating a single table to SAP Data Hub, it is fine to provide one job for “Data Transfer Jobs” and as well for “Calculation Jobs”.
  ![](/SLT/6_JobSettings.png)
1. Click “next” and then “create”.

Note down the **Mass Transfer ID**, that has been generated. This **ID** uniquely identifies the SLT Configuration and is required later for the configuration of the SLT Connector operator.



