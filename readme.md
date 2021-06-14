    #     ___  ____     _    ____ _     _____
    #    / _ \|  _ \   / \  / ___| |   | ____|
    #   | | | | |_) | / _ \| |   | |   |  _|
    #   | |_| |  _ < / ___ | |___| |___| |___
    #    \___/|_| \_/_/   \_\____|_____|_____|
***

# Autonomous Database

Oracle Autonomous database is an inovative platform for data including transactional data, relational, nosql and analytical.

During this time, we will construct a integrated data platform with a transaction application and analytics application.

The main topics that we will execute during this time is:

<a name="#top">Menu:</a>

1. [ Accessing the Oracle Public Cloud ](#1)
2. [ Setup your environment ](#2)
3. [ Provisioning Autonomous Transaction Processing (ATP) ](#3)
4. [ Provisioning Autonomous Data Warehouse (ADW) ](#4)
5. [ Provisioning Oracle Analytics Cloud (OAC) ](#5)
6. [ Create an application on APEX ](#6)
7. [ Loading data to ADW Using Database Actions: Database (ATP) ](#7)
8. [ Loading data to ADW Using Database Actions: Data Lake (Object Storage) ](#8)
9. [ Oracle Machine Learning ](#9)
10. [ Get insights with your data in OML Notebooks ](#10)
11. [ Creating a dashboard on OAC ](#11)

<a name="1"></a>
# 1. Accessing the Oracle Public Cloud
On your web browser, visit the oracle [site](http://www.oracle.com "Oracle Official Site")

![oracle site!](images/01.png "oracle site")

On Oracle website, go to "View accounts":

![oracle site!](images/02.png "oracle site")

![oracle site!](images/03.png "oracle site")

On "View Accounts" click in "Cloud Account" -> "Sign in to cloud":

![oracle site!](images/170.png "oracle site")

![oracle site!](images/171.png "oracle site")

On "Sign in" page, put the information about your cloud account:

![oracle site!](images/172.png "oracle site")

Insert your tenant name here:

![oracle site!](images/173.png "oracle site")

Then click in next:

![oracle site!](images/174.png "oracle site")

At this moment you need to inform your account and password:

![oracle site!](images/175.png "oracle site")

![oracle site!](images/176.png "oracle site")

Then click in next:

![oracle site!](images/12.png "oracle site")

On Console page, you have the menu on the left top of the screen:

![oracle Cloud site!](images/13.png "oracle cloud site")

![oracle cloud site!](images/256.png "oracle Cloud site")

Menu contains all those services that you can use on cloud.

Also you have on the top of your screen the region that you are logged in: 

![oracle cloud site!](images/257.png "oracle Cloud site")

And you have your profile configuration on the top right of main page

![oracle cloud site!](images/16.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="2"></a>
# 2. Setup your environment

## Create a compartment
First you need to create the compartment. To create your compartment, click on menu -> identity -> Compartment

![oracle cloud site!](images/258.png "oracle Cloud site")

Then click in create compartment:

![oracle cloud site!](images/18.png "oracle Cloud site")

Put your information about your compartment:

![oracle cloud site!](images/19.png "oracle Cloud site")

Then click in create.

## Upload files

Second step we will upload the necessary files for this workshop.

We will create a bucket into an object storage.

To create an object storage bucket, click in menu -> Object Storage -> Object storage

![oracle cloud site!](images/259.png "oracle Cloud site")

Make sure that you are in the right compartment:

![oracle cloud site!](images/21.png "oracle Cloud site")

Then click in "Create bucket":

![oracle cloud site!](images/22.png "oracle Cloud site")

On the bucket creation page, insert the name of desired bucket:

![oracle cloud site!](images/260.png "oracle Cloud site")

![oracle cloud site!](images/261.png "oracle Cloud site")

And then click "create bucket":

![oracle cloud site!](images/25.png "oracle Cloud site")

Check if your bucket has been created:

![oracle cloud site!](images/26.png "oracle Cloud site")

Click on your created bucket:

![oracle cloud site!](images/27.png "oracle Cloud site")

>> Download files for this workshop:

>> <a href="https://github.com/erikanagamine/autonomousdatabase/raw/master/files/geonames.json" target="_geonames">geonames.json</a>

>> <a href="https://github.com/erikanagamine/autonomousdatabase/raw/master/files/Global_Landslide_Catalog_Export.csv" target="_landslide">Global_Landslide_Catalog_Export.csv</a>


PS: file Sources - Reference:
<a href="https://catalog.data.gov/dataset/global-landslide-catalog-export" target="_vendas">Nasa - Global Landslide</a>

<a href="https://www.geonames.org/" target="_vendas">Geonames.org</a>


On your bucket page, click in "Upload Objects":

![oracle cloud site!](images/28.png "oracle Cloud site")

On upload page, select the folder or drag and drop the downloaded files:

![oracle cloud site!](images/29.png "oracle Cloud site")

Then click close:

![oracle cloud site!](images/177.png "oracle Cloud site")

Check if files was download correctly:

![oracle cloud site!](images/178.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="3"></a>
# 3. Provisioning Autonomous Transaction Processing (ATP)

In this session we will provision an Autonomous Transaction Processing Database. This database is designed for OLTP.

So, to start the provision, go to menu -> Databases -> Autonomous Transaction Processing:

![oracle cloud site!](images/262.png "oracle Cloud site")

Check if you are on the right compartment:

![oracle cloud site!](images/34.png "oracle Cloud site")

Then Click in "Create Autonomous Database"

![oracle cloud site!](images/34.png "oracle Cloud site")

On the creation page:

![oracle cloud site!](images/179.png "oracle Cloud site")

Check if the follow information was filled:
- Compartment: <check if is correct>
- Display name: <put an name - Example: atpft>
- Database name: <put an name - Example: atpft>
- Choose the workload type: in this case Transaction Processing
- Choose deployment type: Shared infrasctructure

![oracle cloud site!](images/180.png "oracle Cloud site")

Continue choosing this options:
- No Always Free option
- Choose database version: 19c
- OCPU Count: 1
- Storage (TB): 1
- No auto scaling
- Choose the admin Password that you want

![oracle cloud site!](images/263.png "oracle Cloud site")

Options that you need to choose:
- Allow Secure access from everywhere
- Choose licensing type: Byol

And then click in "Create autonomous database":

![oracle cloud site!](images/264.png "oracle Cloud site")

During creation process time, you will see the amber color of word "ATP":

![oracle cloud site!](images/186.png "oracle Cloud site")

When the process finish, the work ATP will change to green:

![oracle cloud site!](images/40.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="4"></a>
# 4. Provisioning Autonomous Data Warehouse (ADW)

In this session we will provision an Autonomous Data Warehouse Database. This database is designed for DW.

So, to start the provision, go to menu -> Databases -> Autonomous Data Warehouse:

![oracle cloud site!](images/41.png "oracle Cloud site")

Check if you are on the right compartment:

![oracle cloud site!](images/34.png "oracle Cloud site")

Then Click in "Create Autonomous Database"

![oracle cloud site!](images/34.png "oracle Cloud site")

On the creation page:

![oracle cloud site!](images/182.png "oracle Cloud site")

Check if the follow information was filled:
- Compartment: <check if is correct>
- Display name: <put an name - Example: adwft>
- Database name: <put an name - Example: adwft>
- Choose the workload type: in this case Data Warehouse
- Choose deployment type: Shared infrasctructure

![oracle cloud site!](images/183.png "oracle Cloud site")

Continue choosing this options:
- No Always Free option
- Choose database version: 19c
- OCPU Count: 1
- Storage (TB): 1
- No auto scaling
- Choose the admin Password that you want

![oracle cloud site!](images/184.png "oracle Cloud site")

Options that you need to choose:
- Allow Secure access from everywhere
- Choose licensing type: Byol

And then click in "Create autonomous database":

![oracle cloud site!](images/185.png "oracle Cloud site")


During creation process time, you will see the amber color of word "ADW":

![oracle cloud site!](images/187.png "oracle Cloud site")

When the process finish, the work ADW will change to green:

![oracle cloud site!](images/48.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="5"></a>
# 5. Provisioning Oracle Analytics Cloud (OAC)

In this section, we will provision the Oracle Analytics Cloud, aka. OAC.

PS. You can download Oracle Analytics Desktop if you are executing in a always free tenant. <a href="https://www.oracle.com/solutions/business-analytics/analytics-desktop/oracle-analytics-desktop.html"> Click here </a> to download (necessary your OTN login)

First, you need to provision the OAC. So on menu, click on "Solutions and Platform" -> Analytics -> Analytics Cloud:

![oracle cloud site!](images/88.png "oracle Cloud site")

Make sure that you have select the right compartment (on the left), and then click on "Create Instance"

![oracle cloud site!](images/89.png "oracle Cloud site")

Input the follow information on the analytics:
- INSTANCE NAME: oac
- DESCRIPTION: My OAC instance
- FEATURE SET: Enterprise Analytics
- CAPACITY: OCPU - 1
- LICENSING: BYOL


Then click in "Create".

![oracle cloud site!](images/188.png "oracle Cloud site")

![oracle cloud site!](images/189.png "oracle Cloud site")

After click in create, the OAC will be provisioned:

![oracle cloud site!](images/91.png "oracle Cloud site")

You can go ahead on next lessons, because the creation will take few minutes.

![oracle cloud site!](images/92.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="6"></a>
# 6. Create an application on APEX

In this step we will create an application based on a spreedsheet in APEX. Oracle Application Express (APEX) is a low code development tool that can enables you to built an application with few steps.

Before start this step, download this file:

>> Download file to proceed in this step:

>> <a href="https://raw.githubusercontent.com/erikanagamine/autonomousdatabase/master/files/citizen.csv" target="_citizen">citizen.csv</a>

We have 2 ways to access APEX: Via Autonomous Database Service or APEX Services.

In this workshop, we will access via APEX Services. So you need to click menu "database related Services" on "APEX Application Development -> APEX Instances"

![oracle cloud site!](images/190.png "oracle Cloud site")

Note that you have 2 APEX services. This services is related to the ADBs created in previous sections. So click on the ATP service on APEX:

![oracle cloud site!](images/191.png "oracle Cloud site")

And then click in "Launch APEX":

![oracle cloud site!](images/192.png "oracle Cloud site")

PS. also you can access the same page on  Autonomous service -> "Service Console" -> Development -> Oracle APEX in Autonomous Console or Autonomous service -> "Tools" -> "APEX"

On the first access on APEX, insert the admin password:

![oracle cloud site!](images/102.png "oracle Cloud site")

And then click on "Sign in to Administration":

![oracle cloud site!](images/103.png "oracle Cloud site")

Now we have to create the workspace for our application. Workspace is a shared logical space for your application.

Click in create workspace:

![oracle cloud site!](images/104.png "oracle Cloud site")

On the creation page, you will need to insert an information:

![oracle cloud site!](images/105.png "oracle Cloud site")

Input the follow information on the APEX Workspace:
- Database User: citizen
- Password: Choose the admin Password that you want
- Workspace name: citizen

Then click in "Create Workspace".

![oracle cloud site!](images/106.png "oracle Cloud site")

![oracle cloud site!](images/193.png "oracle Cloud site")

If your workspace has been create, you should see a message on the top of page:

![oracle cloud site!](images/195.png "oracle Cloud site")

Click on the created workspace:

![oracle cloud site!](images/194.png "oracle Cloud site")

On the workspace login page:

![oracle cloud site!](images/196.png "oracle Cloud site")

Insert the password that you choose for your workspace and then click in "Sign in":

![oracle cloud site!](images/197.png "oracle Cloud site")

On the main page of your workspace:

![oracle cloud site!](images/111.png "oracle Cloud site")

Click in "app builder":

![oracle cloud site!](images/112.png "oracle Cloud site")

![oracle cloud site!](images/113.png "oracle Cloud site")

On the creation app page:

![oracle cloud site!](images/114.png "oracle Cloud site")

Click in "Create an new app":

![oracle cloud site!](images/115.png "oracle Cloud site")

![oracle cloud site!](images/116.png "oracle Cloud site")

Click in "From a file":

![oracle cloud site!](images/117.png "oracle Cloud site")

Drag and drop the file that you have download on beginning of this step:

![oracle cloud site!](images/118.png "oracle Cloud site")

![oracle cloud site!](images/119.png "oracle Cloud site")

Now the APEX will read the file:

![oracle cloud site!](images/120.png "oracle Cloud site")

Insert the name of table as "resident_registry":

![oracle cloud site!](images/198.png "oracle Cloud site")

Review the information and check the parsed information.

![oracle cloud site!](images/199.png "oracle Cloud site")

And then click on "Load Data". If everything works fine, you will se the follow information:

![oracle cloud site!](images/200.png "oracle Cloud site")

Click on "Create Application".

![oracle cloud site!](images/201.png "oracle Cloud site")

On the create application page, click in "add page":

![oracle cloud site!](images/202.png "oracle Cloud site")

And then, click in "Interative Grid":

![oracle cloud site!](images/203.png "oracle Cloud site")

On the Interative grid page , insert the page name as "residents register page" and select the table that contain all data:

![oracle cloud site!](images/204.png "oracle Cloud site")

![oracle cloud site!](images/205.png "oracle Cloud site")

![oracle cloud site!](images/206.png "oracle Cloud site")

Take a look that your form has been create as a page:

![oracle cloud site!](images/207.png "oracle Cloud site")


Check all features in this page:

![oracle cloud site!](images/134.png "oracle Cloud site")

And then, Click in create application:

![oracle cloud site!](images/209.png "oracle Cloud site")

![oracle cloud site!](images/136.png "oracle Cloud site")

After load, you sucessfully create your first application:

![oracle cloud site!](images/137.png "oracle Cloud site")

Execute your application in "Run Application":

![oracle cloud site!](images/138.png "oracle Cloud site")

On your application page, insert the user / password of your application and then click in "Sign in":

![oracle cloud site!](images/210.png "oracle Cloud site")

Notice that your application has the "residents register page", so click on that:

![oracle cloud site!](images/211.png "oracle Cloud site")

You can insert new customers on your grid:

![oracle cloud site!](images/212.png "oracle Cloud site")

![oracle cloud site!](images/213.png "oracle Cloud site")

![oracle cloud site!](images/214.png "oracle Cloud site")

![oracle cloud site!](images/215.png "oracle Cloud site")

![oracle cloud site!](images/216.png "oracle Cloud site")

And you can check some dashboards created by default:

![oracle cloud site!](images/217.png "oracle Cloud site")

So, now you can explore more APEX and create more applications :)


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)

<a name="7"></a>

# 7. Loading data to ADW Using Database Actions: Database (ATP)

At this time we will use the SQL Developer Web (via on Database Actions console) on ADW to connect ATP database.

First we have to copy the ATP wallet to object storage.

On SQL Developer Web, we will load data from files load into object storage. This activity needs an auth token.

## Generate a token to connect your database with files on bucket

In this section we will generate a token to connect the files on object storage with autonomous database.

First access your user data, on the top of screen, click on profile and click on your user:

![oracle cloud site!](images/58.png "oracle Cloud site")

Click in "Auth token" (menu at left of your screen) and then Click on "Generate token":

![oracle cloud site!](images/59.png "oracle Cloud site")

Save this generated token into a file.

![oracle cloud site!](images/60.png "oracle Cloud site")

PS: This token is generated once per time. If you lose this token, you need to create another one.

![oracle cloud site!](images/61.png "oracle Cloud site")

# Generate a wallet on ATP

On ATP main page, click in "DB Connection":

![oracle cloud site!](images/152.png "oracle Cloud site")

You need to select wallet type as "Instance Wallet" and then click in "Download Wallet":

![oracle cloud site!](images/218.png "oracle Cloud site")

So, then insert a password to download the wallet and then click in download:

![oracle cloud site!](images/154.png "oracle Cloud site")

Notice that wallet was a tnsnames, wallet, etc. files.

Decompress the wallet file and get the file called "cwallet.sso":

![oracle cloud site!](images/155.png "oracle Cloud site")

Now you have to insert the "cwallet.sso" to the bucket. The step by step how can you create a bucket and insert files was describe in step 2:

![oracle cloud site!](images/156.png "oracle Cloud site")

# Create credential to load atp wallet to object storage in OCI

First connect to the Database actions on ADW and click in "Tools":

![oracle cloud site!](images/219.png "oracle Cloud site")

Select "Open Database Actions" tool:

![oracle cloud site!](images/220.png "oracle Cloud site")

Insert your admin username then click in "next":

![oracle cloud site!](images/221.png "oracle Cloud site")

Insert your admin password then click in "Sign in":

![oracle cloud site!](images/222.png "oracle Cloud site")

This is the database actions central console. We will click on SQL to create the credential. Credential is neeed for create a connection between Object Storage and Autonomous Database.

![oracle cloud site!](images/223.png "oracle Cloud site")

So, click in SQL:

![oracle cloud site!](images/224.png "oracle Cloud site")

In the first time that you access the sqldeveloper web console you will see some tips that inform you how to use the environment.

![oracle cloud site!](images/225.png "oracle Cloud site")


In this page, the queries can be executed insert the code on (1) and running click in (2) that shows a tabular view or (3) in script view:

![oracle cloud site!](images/150.png "oracle Cloud site")


Now you can edit and copy the information below with your information and execute on SQL Developer Web, using "Run Script" button or F5:

```
-- Create credential
DECLARE 
    v_credential VARCHAR2(100) := 'OCI_CLOUD_STORAGE_CRED'; -- choose the name of your preference
    v_user       VARCHAR2(100) := '<insert your user>'; -- insert here your user, on menu Identity -> Users -> User Details or profile (on the top of your page) -> username (example: oracleidentitycloudservice/myuser@mycompany.com)'; 
    v_password   VARCHAR2(100) := '<insert your token>'; -- on your user page, click in Auth Tokens -> generate Token example: 'h<fMHJiGKVvvgl2uz0[Q';
BEGIN 
  BEGIN
    dbms_cloud.Drop_credential(credential_name => v_credential); 
  EXCEPTION 
    WHEN OTHERS THEN
      null;
  end;
  BEGIN 
          dbms_cloud.Create_credential (credential_name => v_credential, 
                                        username => v_user, 
                                        password => v_password); 
      END; 
END;
/ 
```

If you execute sucessfully, you hit the message below:

![oracle cloud site!](images/151.png "oracle Cloud site")

PS. If you receive the message "ORA-20000: ORA-29283: invalid file operation: nonexistent file or path [29434]..." regenerate your token.


Now we can connect download the wallet from ATP to ADW:

```
DECLARE
  v_region      varchar2(30) :=    '<your region>'; --'insert here a region, exemple us-ashburn-1';
  v_namespace   varchar2(30) :=    '<your namespace>'; --'console cloud-> Object Storage -> Bucket Details-> <namespace>';
  v_bucket      varchar2(30) :=    '<your bucket>'; --'console cloud-> Object Storage -> Bucket Details exemple: Workshop_Object';
  v_credential  VARCHAR2(100) := 'OCI_CLOUD_STORAGE_CRED';
  v_url         varchar2(4000);

BEGIN
  v_url := 'https://objectstorage.'||v_region||'.oraclecloud.com/n/'||v_namespace||'/b/'||v_bucket||'/o/cwallet.sso';
  
DBMS_CLOUD.GET_OBJECT(
credential_name => v_credential,
object_uri => v_url,
directory_name => 'DATA_PUMP_DIR');
END;
/

```
![oracle cloud site!](images/157.png "oracle Cloud site")

# Create credential to access the database via Database Link (DBlink)

Warning: in this step the credential was the database user / password from source database ATP to connect ADW instance, not the token:

```

DECLARE
  v_db_usr           varchar2(30) :=    '<your db username >'; --database username, for example ADMIN
  v_password_db_usr  varchar2(30) :=    '<your db Password>'; -- password for database connection
  v_credential_db    varchar2(30) :=    '<your db credential name >'; -- database credential name, for example:DB_LINK_CRED_ATP
BEGIN
  BEGIN
    dbms_cloud.Drop_credential(credential_name => v_credential_db); 
  EXCEPTION 
    WHEN OTHERS THEN
      null;
  end;

DBMS_CLOUD.CREATE_CREDENTIAL(
credential_name => v_credential_db,
username => v_db_usr, 
password => v_password_db_usr
);
END;
/

```

![oracle cloud site!](images/158.png "oracle Cloud site")

Now you can create the database link to ATP. Most of those information you can check in the tnsnames.ora that you download previosly.

PS: the tnsnames contain the information that you need below such as service name, ssl certificate and the region. Choose the best service:

![oracle cloud site!](images/226.png "oracle Cloud site")

Now, replace the information that you found on tnsnames on the block below:

```
DECLARE
  v_database_link   varchar2(30)  :='< your database link name > '; -- your database link name, for example: ATP_LINK
  v_hostname        varchar2(1000) :=    '<your hostname>'; --'insert here your hostname, example adb.us-ashburn-1.oraclecloud.com';
  v_credential_db   varchar2(100) :=    '<your db credential name >'; -- database credential name, for example:DB_LINK_CRED_ATP
  v_service_name    varchar2(100) := '<your service name from tnsnames>'; -- tnsnames service name, for example: t17xdtmmzvuylh3_atpft_low.adb.oraclecloud.com
  v_cert_ssl        varchar2(1000) := '<certificate in tnsnames>'; -- your certification in TNSNAMES: example CN=adwc.uscom-east-1.oraclecloud.com,OU=Oracle BMCS US,O=Oracle Corporation,L=Redwood City,ST=California,C=US
  v_db_port         varchar2(10)   := '< tnsnames db port >'; -- your db port in tnsnames
  
BEGIN
   BEGIN
	   DBMS_CLOUD_ADMIN.DROP_DATABASE_LINK(db_link_name => v_database_link );
   EXCEPTION
     WHEN OTHERS THEN
       NULL;
   END;

  BEGIN
    DBMS_CLOUD_ADMIN.CREATE_DATABASE_LINK(
      db_link_name => v_database_link,
      hostname => v_hostname,
      port => v_db_port,
      service_name =>   v_service_name,
      ssl_server_cert_dn => v_cert_ssl,
      credential_name => v_credential_db,
      directory_name => 'DATA_PUMP_DIR');
  END;
END;
/

```

![oracle cloud site!](images/227.png "oracle Cloud site")

Execute a query to test the connection to ADW:

```
select * from all_objects@ATP_LINK where owner='CITIZEN';

```

![oracle cloud site!](images/160.png "oracle Cloud site")


Execute a query to test the connection to ATP (observe that we insert the information about table load on APEX):

```
select * from all_tables@ATP_LINK where table_name='RESIDENT_REGISTRY' and owner='CITIZEN';

```

![oracle cloud site!](images/166.png "oracle Cloud site")


Now you can access data between ATP in ADW!!!



<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="8"></a>

# 8. Loading data to ADW Using Database Actions: Data Lake (Object Storage)

On database actions, we will load data from files load into object storage. This activity needs an auth token. This auth token can be the same as used in the previous task.

You need to use your ADW for this steps.

## Generate a token to connect your database with files on bucket

In this section we will generate a token to connect the files on object storage with autonomous database. 

First access your user data, on the top of screen, click on profile and click on your user:

![oracle cloud site!](images/58.png "oracle Cloud site")

Click in "Auth token" (menu at left of your screen) and then Click on "Generate token":

![oracle cloud site!](images/59.png "oracle Cloud site")

Save this generated token into a file.

![oracle cloud site!](images/60.png "oracle Cloud site")

PS: This token is generated once per time. If you lose this token, you need to create another one.

![oracle cloud site!](images/61.png "oracle Cloud site")

## Upload bucket files on SQL Developer Web


First we need to access the SQL Developer Web in ADW. So, to access this tool, go to menu -> Databases -> Autonomous Data Warehouse -> tools -> database actions

First connect to the Database actions on ADW and click in "Tools":

![oracle cloud site!](images/219.png "oracle Cloud site")

Select "Open Database Actions" tool:

![oracle cloud site!](images/220.png "oracle Cloud site")

Insert your admin username then click in "next":

![oracle cloud site!](images/221.png "oracle Cloud site")

Insert your admin password then click in "Sign in":

![oracle cloud site!](images/222.png "oracle Cloud site")

This is the database actions central console. We will click on SQL to create the credential. Credential is neeed for create a connection between Object Storage and Autonomous Database.

![oracle cloud site!](images/223.png "oracle Cloud site")

# Create credential to load data from object storage

This step is the same of [ Step 7: connect database via Dblink ](#7).

If you already did the token generation + create OCI CLOUD Storage Credential, you don't need to do it again.

So, go ahead with next steps.

# Load data via database actions

![oracle cloud site!](images/228.png "oracle Cloud site")

On database actions central console click in "Data Load":

![oracle cloud site!](images/229.png "oracle Cloud site")

On data load page you have two methods get the data:
- Load data you will load the data to autonomous. This is good if you have a frequency data access in the autonomous.
- Link Data: This option is for data that you need to access and doesn't store in autonomous.

Also you have this 3 methods to receive source data on autonomous:
- local file: if you need to load a file from your computer, you choose this option
- database: if you need to load data from another database to autonomous, you can choose this option.
- Cloud Storage: if you need to load data from a cloud storage (OCI object storage you choose this option)

![oracle cloud site!](images/230.png "oracle Cloud site")

In this time we will use files that we store on Object storage in the step 2 [ Return to step 2 ](#2) :
- geonames.json: we will access via link data option
- Global_Landslide_Catalog_Export.csv: we wiil load data

# Load data from object storage into autonomous database via Database Actions as link data

At this time we will load geonames.json file stored on Object Storage via link data option. So in the Data load page select link data -> cloud storage and then next.

![oracle cloud site!](images/231.png "oracle Cloud site")

In the link cloud object page you will see a message to setup cloud storage. So, click in OK

![oracle cloud site!](images/232.png "oracle Cloud site")

On setup cloud storage you will see this page:

![oracle cloud site!](images/233.png "oracle Cloud site")

So add the follow information to load the data:
- name: name of job
- Cloud Storage: Oracle
- URI+Bucket: your cloud storage, example: https://objectstorage.us-ashburn-1.oraclecloud.com/n/<namespace>/b/<name of bucket>/o/ -- you can get this information on bucket page
- Credential: select credential -> choose the credential that you insert in the activities before. 

and then click in test:

![oracle cloud site!](images/234.png "oracle Cloud site")

click in create:

![oracle cloud site!](images/234.png "oracle Cloud site")

Note that you found the json file that you store on the object storage. So click in the file and drag to the other screen:

![oracle cloud site!](images/235.png "oracle Cloud site")

Edit the job (in pencil icon) before click in play and modify all fields to varchar2(4000) as image below:

![oracle cloud site!](images/255.png "oracle Cloud site")

Click in play:

![oracle cloud site!](images/235.png "oracle Cloud site")

and ok to execute the job:

![oracle cloud site!](images/236.png "oracle Cloud site")


Now check the progress of job

![oracle cloud site!](images/237.png "oracle Cloud site")

![oracle cloud site!](images/238.png "oracle Cloud site")

![oracle cloud site!](images/239.png "oracle Cloud site")

If everything run sucessfully, you will see the check in the job as below:

![oracle cloud site!](images/240.png "oracle Cloud site")

Now you can see the view geodata in the sql developer web option:

![oracle cloud site!](images/241.png "oracle Cloud site")


# Load data from object storage to autonomous database via Database Actions as load data to autonomous storage

To load data from object storage to autonomous in Database Actions, click in load data -> cloud storage and then next:

![oracle cloud site!](images/242.png "oracle Cloud site")

Drag the landslide file:

![oracle cloud site!](images/243.png "oracle Cloud site")

And then click in play:

![oracle cloud site!](images/244.png "oracle Cloud site")

click in ok to run the job:

![oracle cloud site!](images/245.png "oracle Cloud site")

Check the progress of job (it will take a minute to load):

![oracle cloud site!](images/246.png "oracle Cloud site")

If everything is good on running job, you see the message below:

![oracle cloud site!](images/247.png "oracle Cloud site")

Now you can see the dataset table load in the sql developer web option:

![oracle cloud site!](images/248.png "oracle Cloud site")

![oracle cloud site!](images/249.png "oracle Cloud site")

Grant tables and create synonym to public:

```
grant select on GLOBAL_LANDSLIDE_CATALOG_EXPORT to public;
grant select on geonames to public;

create public synonym GLOBAL_LANDSLIDE_CATALOG_EXPORT for admin.GLOBAL_LANDSLIDE_CATALOG_EXPORT;
create public synonym geonames for admin.geonames;

```


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)

<a name="9"></a>

# 9. Oracle Machine Learning

The Oracle Machine Learning is an Apache Zeppelin notebook that can help you to know your data.

At this time we will create an user for this tool and can be used in ADW or ATP.

In this workshop, we will create on ADW. Select your ADW on menu page:

![oracle cloud site!](images/41.png "oracle Cloud site")

In the ADW page, select your ADW:

![oracle cloud site!](images/49.png "oracle Cloud site")

Click on "tools" tab:

![oracle cloud site!](images/50.png "oracle Cloud site")

Then click on "Oracle ML User Administration": 

![oracle cloud site!](images/51.png "oracle Cloud site")

On the ML administration page, insert admin as username and the password that you create for admin on ADW creation:

![oracle cloud site!](images/52.png "oracle Cloud site")

Then click in "Sign In":

![oracle cloud site!](images/53.png "oracle Cloud site")

On the ML user administration main page, click in "create" 

![oracle cloud site!](images/54.png "oracle Cloud site")

Insert data from your user:

![oracle cloud site!](images/55.png "oracle Cloud site")

Then click in create:

![oracle cloud site!](images/56.png "oracle Cloud site")

Check if your user has been created:

![oracle cloud site!](images/57.png "oracle Cloud site")

PS: remember the user create and password. You will use this on step 10.

<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)

<a name="10"></a>

# 10. Get insights with your data in OML Notebooks

If you need to see your data in another visualization using notebooks, you can use Oracle Machine Learning.

Oracle Machine Learning is a platform that possibility you discover your data without necessity of another tool.

On ADW console, click in "Service Console":

![oracle cloud site!](images/75.png "oracle Cloud site")

On service console, click in "Development":

![oracle cloud site!](images/76.png "oracle Cloud site")

Under development tab, click in "Oracle Machine Learning Notebooks":

![oracle cloud site!](images/77.png "oracle Cloud site")

Insert your user data (as you do on step 7):

![oracle cloud site!](images/78.png "oracle Cloud site")

Then click "Sign In":

![oracle cloud site!](images/78.png "oracle Cloud site")

On the main page of OML Notebooks, let's create our own notebook:

![oracle cloud site!](images/79.png "oracle Cloud site")

Click in notebooks:

![oracle cloud site!](images/80.png "oracle Cloud site")

On notebooks page, click in "Create":

![oracle cloud site!](images/81.png "oracle Cloud site")

On creation page, insert a name for your notebook, then click ok:

![oracle cloud site!](images/82.png "oracle Cloud site")

![oracle cloud site!](images/83.png "oracle Cloud site")

On notebook page, you can explore more your data:

![oracle cloud site!](images/84.png "oracle Cloud site")

Execute this in script mode:
```
%script

select * from geonames

```

![oracle cloud site!](images/250.png "oracle Cloud site")


Execute this select in sql mode:

```
%sql

select * from GLOBAL_LANDSLIDE_CATALOG_EXPORT

```
![oracle cloud site!](images/251.png "oracle Cloud site")

Notice that we have more options to visualize data in SQL:

![oracle cloud site!](images/252.png "oracle Cloud site")

![oracle cloud site!](images/254.png "oracle Cloud site")

Tip: there is a lots of examples of using OML. Please check in the example page inside the notebook. Also you can use python:

![oracle cloud site!](images/253.png "oracle Cloud site")



<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="11"></a>

# 10. Creating a dashboard on OAC

Before create a dashboard you need to connect your Database instance to the OAC. To connect your instance in OAC, go to OAC Page:

![oracle cloud site!](images/93.png "oracle Cloud site")


And then click on "Open URL":

![oracle cloud site!](images/94.png "oracle Cloud site")

So, on the OAC page, click in create:

![oracle cloud site!](images/95.png "oracle Cloud site")

and then, click in "Connection":

![oracle cloud site!](images/96.png "oracle Cloud site")

Select the property connection for ADW (autonomous data warehouse):

![oracle cloud site!](images/97.png "oracle Cloud site")

Input your connection information:

![oracle cloud site!](images/98.png "oracle Cloud site")

and then click in save:

![oracle cloud site!](images/99.png "oracle Cloud site")

So, now you have sucessfully connect your ADW with your OAC! :-)



<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)



