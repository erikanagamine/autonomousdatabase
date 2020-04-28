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
2. [ Setup base Environment ](#2)
3. [ Provisioning Autonomous Transaction Processing (ATP) ](#3)
4. [ Provisioning Autonomous Data Warehouse (ADW) ](#4)
5. [ Provisioning Oracle Analytics Cloud (OAC) ](#5)
6. [ Create an application on APEX ](#6)
7. [ Import data from object storage ](#7)
8. [ Creating a dashboard on OAC ](#8)

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
# 2. Setup your Environment

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

In this session we will provision an Autonomous database Transaction Processing. This database is designed for OLTP.

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
# 7. Import data from object storage

## Generate a token to connect your database with files on bucket

In this section we will generate a token to connect the files on object storage with autonomous database. 



<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


<a name="8"></a>
# 8. Creating a dashboard on OAC

<!-- blank line -->
----
<!-- blank line -->

[ Return to top ](#top)


```
::: sql
%sql
dbms_cloud.Create_credential (credential_name => v_credencial, username => v_usuario, password => v_senha); 

```

