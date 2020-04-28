    #     ___  ____     _    ____ _     _____
    #    / _ \|  _ \   / \  / ___| |   | ____|
    #   | | | | |_) | / _ \| |   | |   |  _|
    #   | |_| |  _ < / ___ | |___| |___| |___
    #    \___/|_| \_/_/   \_\____|_____|_____|
***

# Autonomous Database

Oracle Autonomous database is an inovative platform for data, including for transaction and analytics data.

During this time, we will construct a integrated data platform with a transaction application and analytics application.

The main topics that we will execute during this time is:

<a name="#top">Menu:</a>

1. [ Accessing the Oracle Public Cloud ](#1)
2. [ Setup your environment ](#2)
3. [ Provisioning Autonomous Transaction Processing (ATP) ](#3)
4. [ Provisioning Autonomous Data Warehouse (ADW) ](#4)
5. [ Provisioning Oracle Analytics Cloud (OAC) ](#5)
6. [ Create an application on APEX ](#6)
7. [ Oracle Machine Learning ](#7)
8. [ SQL Developer Web ](#8)
9. [ Know your data using OML Notebooks ](#9)
10. [ Creating a dashboard on OAC ](#10)

<a name="1"></a>
# 1. Accessing the Oracle Public Cloud
On your web browser, visit the oracle [site](http://www.oracle.com "Oracle Official Site")

![oracle site!](images/01.png "oracle site")

On Oracle website, go to "View accounts":

![oracle site!](images/02.png "oracle site")

![oracle site!](images/03.png "oracle site")

On "View Accounts" click in "Sign in to cloud":

![oracle site!](images/04.png "oracle site")

![oracle site!](images/05.png "oracle site")

On "Sign in" page, put the information about your cloud account:

![oracle site!](images/06.png "oracle site")

![oracle site!](images/07.png "oracle site")

Then click in next:

![oracle site!](images/08.png "oracle site")

![oracle site!](images/09.png "oracle site")

At this moment you need to inform your account and password:

![oracle site!](images/10.png "oracle site")

![oracle site!](images/11.png "oracle site")

Then click in next:

![oracle site!](images/12.png "oracle site")

On Console page, you have the menu on the left top of the screen:

![oracle Cloud site!](images/13.png "oracle cloud site")

![oracle cloud site!](images/14.png "oracle Cloud site")

Menu contains all those services that you can use on cloud.

Also you have on the top of your screen the region that you are logged in: 

![oracle cloud site!](images/15.png "oracle Cloud site")

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

![oracle cloud site!](images/17.png "oracle Cloud site")

Then click in create compartment:

![oracle cloud site!](images/18.png "oracle Cloud site")

Put your information about your compartment:

![oracle cloud site!](images/19.png "oracle Cloud site")

Then click in create.

## Upload files

Second step we will upload the necessary files for this workshop.

We will create a bucket into an object storage.

To create an object storage bucket, click in menu -> Object Storage -> Object storage

![oracle cloud site!](images/20.png "oracle Cloud site")

Make sure that you are in the right compartment:

![oracle cloud site!](images/21.png "oracle Cloud site")

Then click in "Create bucket":

![oracle cloud site!](images/22.png "oracle Cloud site")

On the bucket creation page, insert the name of desired bucket:

![oracle cloud site!](images/23.png "oracle Cloud site")

![oracle cloud site!](images/24.png "oracle Cloud site")

And then click "create bucket":

![oracle cloud site!](images/25.png "oracle Cloud site")

Check if your bucket has been created:

![oracle cloud site!](images/26.png "oracle Cloud site")

Click on your created bucket:

![oracle cloud site!](images/27.png "oracle Cloud site")

>> Download files for this workshop:

>> <a href="https://github.com/erikanagamine/autonomousdatabase/raw/master/files/Vendas.csv">Vendas.csv</a>

>> <a href="https://github.com/erikanagamine/autonomousdatabase/raw/master/files/dimensao_produto.csv">dimensao_produto.csv</a>

On your bucket page, click in "Upload Objects":

![oracle cloud site!](images/28.png "oracle Cloud site")

On upload page, select the folder or drag and drop the downloaded files:

![oracle cloud site!](images/29.png "oracle Cloud site")

Then click ok:

![oracle cloud site!](images/30.png "oracle Cloud site")

Check if files was download correctly:

![oracle cloud site!](images/31.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="3"></a>
# 3. Provisioning Autonomous Transaction Processing (ATP)

In this session we will provision an Autonomous Transaction Processing Database. This database is designed for OLTP.

So, to start the provision, go to menu -> Databases -> Autonomous Transaction Processing:

![oracle cloud site!](images/32.png "oracle Cloud site")

Check if you are on the right compartment:

![oracle cloud site!](images/34.png "oracle Cloud site")

Then Click in "Create Autonomous Database"

![oracle cloud site!](images/34.png "oracle Cloud site")

On the creation page:

![oracle cloud site!](images/35.png "oracle Cloud site")

Check if the follow information was filled:
- Compartment: <check if is correct>
- Display name: <put an name - Example: atp>
- Database name: <put an name - Example: atp>
- Choose the workload type: in this case Transaction Processing
- Choose deployment type: Shared infrasctructure

![oracle cloud site!](images/36.png "oracle Cloud site")

Continue choosing this options:
- No Always Free option
- Choose database version: 18c
- OCPU Count: 1
- Storage (TB): 1
- No auto scaling
- Choose the admin Password that you want

![oracle cloud site!](images/37.png "oracle Cloud site")

Options that you need to choose:
- Allow Secure access from everywhere
- Choose licensing type: Byol

And then click in "Create autonomous database":

![oracle cloud site!](images/38.png "oracle Cloud site")

During creation process time, you will see the amber color of word "ATP":

![oracle cloud site!](images/39.png "oracle Cloud site")

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

![oracle cloud site!](images/42.png "oracle Cloud site")

Check if the follow information was filled:
- Compartment: <check if is correct>
- Display name: <put an name - Example: adw1>
- Database name: <put an name - Example: adw1>
- Choose the workload type: in this case Data Warehouse
- Choose deployment type: Shared infrasctructure

![oracle cloud site!](images/43.png "oracle Cloud site")

Continue choosing this options:
- No Always Free option
- Choose database version: 18c
- OCPU Count: 1
- Storage (TB): 1
- No auto scaling
- Choose the admin Password that you want

![oracle cloud site!](images/44.png "oracle Cloud site")

Options that you need to choose:
- Allow Secure access from everywhere
- Choose licensing type: Byol

And then click in "Create autonomous database":

![oracle cloud site!](images/45.png "oracle Cloud site")

![oracle cloud site!](images/46.png "oracle Cloud site")

During creation process time, you will see the amber color of word "ADW":

![oracle cloud site!](images/47.png "oracle Cloud site")

When the process finish, the work ADW will change to green:

![oracle cloud site!](images/48.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="5"></a>
# 5. Provisioning Oracle Analytics Cloud (OAC)

<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="6"></a>
# 6. Create an application on APEX

<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)

<a name="7"></a>
# 7. Oracle Machine Learning

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

PS: remember the user create and password. You will use this on step 9.

<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)

<a name="8"></a>
# 8. SQL Developer Web

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

## Upload bucket files on SQL Developer Web

First we need to access the SQL Developer Web in ADW. So, to access this tool, go to menu -> Databases -> Autonomous Data Warehouse:

![oracle cloud site!](images/41.png "oracle Cloud site")

Check if you are on the right compartment:

![oracle cloud site!](images/34.png "oracle Cloud site")

In the ADW page, select your ADW:

![oracle cloud site!](images/49.png "oracle Cloud site")

Click on "tools" tab:

![oracle cloud site!](images/50.png "oracle Cloud site")

And then, click on SQL Developer Web:

![oracle cloud site!](images/62.png "oracle Cloud site")

Under SQL Developer Web tab, insert your user as admin and password:

![oracle cloud site!](images/63.png "oracle Cloud site")

And then click in "Sign In":

![oracle cloud site!](images/64.png "oracle Cloud site")

Congratulations! You logged on SQL Developer!

![oracle cloud site!](images/65.png "oracle Cloud site")

# Create credential to load data from object storage

On the main page of SQL Developer Web, you can execute the queries:

![oracle cloud site!](images/67.png "oracle Cloud site")

Now you can edit and copy the information below with your information and execute on SQL Developer Web, using "Run Script" button or F5:

```
-- Create credential
DECLARE 
    v_credential VARCHAR2(100) := 'OBJ_STORAGE_DATA'; 
    v_user       VARCHAR2(100) := '<insert your user>'; -- example: 'oracleidentitycloudservice/meuusuario@meuemail.com'; 
    v_password   VARCHAR2(100) := '<insert your token'; -- example: 'h<fMHJiGKVvvgl2uz0[Q';
BEGIN 
    dbms_cloud.Drop_credential(credential_name => v_credential); 
EXCEPTION 
    WHEN OTHERS THEN 
      BEGIN 
          dbms_cloud.Create_credential (credential_name => v_credential, 
                                        username => v_user,
                                        password => v_password); 
      END; 
END;
/ 
```

If you execute sucessfully, you hit the message below:

![oracle cloud site!](images/68.png "oracle Cloud site")

Then Create table called "vendas":

```
    CREATE TABLE vendas 
      ( 
         id          NUMBER, 
         id_cliente  NUMBER, 
         id_pedido   NUMBER, 
         id_produto  NUMBER, 
         data_pedido DATE, 
         valor       NUMBER(38, 2), 
         quantidade  NUMBER, 
         valor_total NUMBER(38, 2), 
         canal       VARCHAR2(50), 
         unidade     VARCHAR2(300), 
         latitude    VARCHAR2(20), 
         longitude   VARCHAR2(20) 
      ); 

```

![oracle cloud site!](images/69.png "oracle Cloud site")


```
declare
  v_region      varchar2(30) :=    '<your region>'; --'coloque aqui a region, exemplo us-phoenix-1';
  v_namespace   varchar2(30) :=    '<your namespace>'; --'console cloud-> Object Storage -> Bucket Details-> <namespace>';
  v_bucket      varchar2(30) :=    '<your bucket>'; --'console cloud-> Object Storage -> Bucket Details exemplo: Workshop_Object';
  v_table_name  varchar2(30) := 'APPDW.VENDAS';
  v_data_source varchar2(100) := 'vendas.csv';
  v_credential  VARCHAR2(100) := 'OBJ_STORAGE_DATA';
  v_url         varchar2(4000);
  
begin
    v_url := 'https://swiftobjectstorage.'||v_region||'.oraclecloud.com/v1/'||v_namespace||'/'||v_bucket||'/'||v_data_source;
  
  dbms_output.put_line(v_url);
  
   DBMS_CLOUD.COPY_DATA(
    table_name => v_table_name,
    credential_name => v_credential,
    file_uri_list =>v_url,
format => json_object('ignoremissingcolumns' value 'true','removequotes' value 'true', 'delimiter' value ',', 'skipheaders' value '1', 'dateformat' value 'MM/DD/YYYY')
);
END;
/

```

![oracle cloud site!](images/70.png "oracle Cloud site")


```
declare
  v_region      varchar2(30) :=    '<your region>'; --'coloque aqui a region, exemplo us-phoenix-1';
  v_namespace   varchar2(30) :=    '<your namespace>'; --'console cloud-> Object Storage -> Bucket Details-> <namespace>';
  v_bucket      varchar2(30) :=    '<your bucket>'; --'console cloud-> Object Storage -> Bucket Details exemplo: Workshop_Object';
  v_table_name  varchar2(30) := 'PRODUTOS';
  v_data_source varchar2(100) := 'dimensao_produto.csv';
  v_credential  VARCHAR2(100) := 'OBJ_STORAGE_DATA';
  v_url        varchar2(4000);
begin
  
   v_url := 'https://swiftobjectstorage.'||v_region||'.oraclecloud.com/v1/'||v_namespace||'/'||v_bucket||'/'||v_data_source;
  
   dbms_output.put_line(v_url);
  
   DBMS_CLOUD.CREATE_EXTERNAL_TABLE(
    table_name => v_table_name,
    credential_name => v_credential,
    file_uri_list => v_url,
    format => json_object('delimiter' value ',','skipheaders' value '1'),
    column_list => 'ID_PRODUTO NUMBER,
    CATEGORIA_PRODUTO VARCHAR(50),
    PRODUTO VARCHAR(100)'
 );
END;
/
```
![oracle cloud site!](images/71.png "oracle Cloud site")


Check if your data have been loaded on tables:

```
select * from produtos;

```

![oracle cloud site!](images/72.png "oracle Cloud site")

```
select * from vendas;

```

![oracle cloud site!](images/73.png "oracle Cloud site")

PS.: For next steps, if you create a different user for Oracle Machine Learning, you need to give the permissions to read tables in another owner:

```
grant select on produtos to appdw;
grant select on vendas to appdw;

```

![oracle cloud site!](images/74.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)

<a name="9"></a>
# 9. Know your data using OML Notebooks

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

On notebook page, you can do selects and visualize your data

![oracle cloud site!](images/84.png "oracle Cloud site")

![oracle cloud site!](images/85.png "oracle Cloud site")

```
%script

select p.produto PRODUTO, sum(v.valor) VALOR_TOTAL, sum(v.quantidade) QUANTIDADE
from admin.vendas v inner join admin.produtos p
on v.id_produto = p.id_produto
group by p.produto;

```

![oracle cloud site!](images/86.png "oracle Cloud site")

![oracle cloud site!](images/87.png "oracle Cloud site")


<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="10"></a>
# 10. Creating a dashboard on OAC

<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)



