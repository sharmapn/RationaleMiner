# RationaleMiner
**Replication Package for Rationale Miner** - Using the rationale Miner requires configuring the database (in MySQL) and the code (Java). <br/>
In brief, the basic tasks in these two parts are as follows.  

A. Database <br/>
-install the required version of the MySQL DBMS <br/>
-restore the ‘peps_new’ database <br/>

B. Code <br/>
-install the Eclipse IDE for the code, and <br/>
-configure the projects in Eclipse <br/>
-copy the libraries (_available as a zip file_) to a 'lib' directory <br/>

The Chart generation 


In detail, the steps to set up the Database and code are as follows.

**A. Database**

The database is named `peps_new'. A 6GB zipfile is hosted on kaggle at this address. It contains the entire MySQL data directory 
and when unzipped is 35GB in size. <br/>
This is easiest way to recreate the MySQL database: to recover the database on another machine. <br/>
For this carry out the following steps: <br/>
1. First install the MySQL Community Server database version 5.6.25 from this link https://downloads.mysql.com/archives/community/. 
Choose the Product version 5.6.25, Microsoft Windows, and Windows (x86, 64 bit).
While installing the database, in the 'Setup Type' screen, <br/> 
(a) choose Full installation, and <br/>
(b) retain the default 'Installation Path' and 'Data Path' <br/> 
(c) Install any sample or system databases that come with it. <br/>
(d) ensure the root user password is root
As a guide you can follow the steps from this tutorial: https://www.mysqltutorial.org/install-mysql/.  <br/>
Though, in this guide the installation is carried out using MySQL installer and where the MySQL software is automatically downloaded.  <br/>
As in our approach, we directly install the software from the (https://downloads.mysql.com/archives/community/) website,  <br/>
thus Step 3 is not required and wont be part of the installation steps, <br/>

2. Download the `data` folder containing the database files for the 'peps_new' database and other MySQL database. <br/>
Stop the MySQL database service. <br/>
Store this folder in the MySQL data directory **replacing the existing 'data' folder**. <br/>
For instance, on my computer, this 'data' folder is in the following directory `C:\ProgramData\MySQL\MySQL Server 5.6\data`.

3. Then you have to recover this database.  First shutdown the MySQL database. 
   Then add the following lines in the `my.ini` file (on my machine, it exists in `C:\ProgramData\MySQL\MySQL Server 5.6` directory), and save the file.

   `innodb_force_recovery=1` 

   Then start the database via the Windows service and the database will be recovered. 
   
   Then stop the database, comment the above line and start the database again. 
   This will start the database in normal mode, and it will be ready for queries. 

**B. Code**

The code consists of two aspects. The Java code and the dependent libraries. 
The Java code is run using the Eclipse IDE. 

1. The libraries are large and are hosted at the. These can be put in any directory and imported as Java

2. The code is hosted within this repository. 
