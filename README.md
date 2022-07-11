# RationaleMiner
Replication Package for Rationale Miner

The rationale Miner consists of two parts: the database (in MySQL format) and the Rationale Miner code (in Java).

A. Database

The database is names `peps_new' and is 35GB in size and is hosted on kaggle at this address. 
The easiest way to recreate the MySQL database is to recover the database on another machine. 
For this carry out the following steps: 
1. First install the MySQL database version 5.6.25 from this link https://downloads.mysql.com/archives/community/. 
Choose the Product version 5.6.25, Microsoft Windows, and Windows (x86, 64 bit).
In doing so install any databases that come with it.
2. Download the `peps_new' database files and store this in the MySQL data directory. For instance, on my computer, this 'data'
is in the folling folder 'D:\ProgramData\MySQL\MySQL Server 5.6\data'
3. Then you have to recover this database.  First shutdown the MySQL database. 
   Then add the following lines in the 'my.ini' file, and save the file.
   innodb_force_recovery=1 
   Then start the database. The database will be recovered. 
   Then stop the database, comment the above line and start it again - this will start the database in normal mode.

B. Code
The code consists of two aspects. The Java code and the dependent libraries. 
The Java code is run using the Eclipse IDE. 

1. The libraries are large and are hosted at the. These can be put in any directory and imported as Java

2. The code is hosted within this repository. 
