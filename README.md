# RationaleMiner
**Replication Package for Rationale Miner** - Using the rationale Miner requires configuring the database (in MySQL) and the code (Java). <br/>
In brief, the basic tasks in these two parts are as follows.  

A. Database <br/>
  - install the required version of the MySQL DBMS <br/>
  - restore the ‘peps_new’ database <br/>

B. Code <br/>
  - install the Eclipse IDE for the code, and <br/>
  - configure the projects in Eclipse <br/>
  - copy the libraries (_available as a zip file_) to a 'lib' directory <br/>

C. Generating the results. This includes the following aspects: <br/>
  - The Chart generation 


In detail, the steps to set up the Database and code are as follows.

**A. Database Installation and Setup**

The database is named `peps_new'. A 6GB zipfile is hosted on kaggle at this address. It contains the entire MySQL data directory 
and when unzipped is 35GB in size. <br/>
This is easiest way to recreate the MySQL database: to recover the database on another machine. <br/>
For this carry out the following steps: <br/>
1. First install the MySQL Community Server database version 5.6.25 from this link https://downloads.mysql.com/archives/community/. 
Choose the Product version 5.6.25, Microsoft Windows, and Windows (x86, 64 bit).
While installing the database, in the 'Setup Type' screen, <br/> 
   - choose Full installation, and <br/>
   - retain the default 'Installation Path' `C:\Program Files\MySQL\` , and default 'Data Path' as `C:\ProgramData\MySQL\MySQL Server 5.6\data` <br/> 
   - Install any sample or system databases that come with it. <br/>
   - ensure the `root` user password is `root` <br/>
As a guide you can follow the steps from this tutorial: `https://www.mysqltutorial.org/install-mysql/`.  <br/>
However, in this guide the installation is carried out using MySQL installer and where the MySQL software is automatically downloaded,   <br/>
while in our approach, we directly install the software from the (`https://downloads.mysql.com/archives/community/`) website,  <br/>
and therefore Step 3 is not required and wont be part of the installation steps, <br/>

2. Download the `data` folder containing the database files for the 'peps_new' database and other MySQL database from here: <br/>
`www.kaggle.com/dataset/d2080fe971b71e11afe1d92688953f27423b0631a669e3a0bdc69e6e813b386e`

  Then, stop the MySQL database service. <br/>
  In the `C:\ProgramData\MySQL\MySQL Server 5.6\data` directory of your machine, rename the existing `data` folder to some other name, e.g. `dataOriginal`
  Store the downloaded folder in the MySQL data directory **thus, we replace the existing 'data' folder**. <br/>
  For instance, on my computer, this 'data' folder is in the following directory `C:\ProgramData\MySQL\MySQL Server 5.6\data`.

3. Then you have to recover this database.  First shutdown the MySQL database. 
   Then add the following lines in the `my.ini` file (on my machine, it exists in `C:\ProgramData\MySQL\MySQL Server 5.6` directory), and save the file.

   `innodb_force_recovery=1` 

   Then start the database via the Windows service and the database will be recovered. 
   
   Then stop the database, comment the above line and start the database again. 
   This will start the database in normal mode, and it will be ready for queries. 

**B. Code**

The Rationale Miner tool is part of the DeMap Miner tool. Thus, it exists as a separate project within the `https://github.com/sharmapn/DeMaPMiner` repository. 
However, all the code (i.e. projects) within the DeMap Miner repository is needed to execute the Rationale Miner tool, as some code from other projects are referenced. 

1. Download all the code from the `https://github.com/sharmapn/DeMaPMiner` repository. <br/>
Then, create a folder named `C:\DeMapMiner` folder and transfer the code in that directory. <br/>
The DeMap Miner folder consists of; <br/>
   - the Java code for the Rationale Miner  in the `DeMap Miner\workspace\rationaleMiner` <br/>
   - the dependent libraries in the `lib` folder <br/>
   - the input and output files in the `` <br/>

2. The Java code is run using the Eclipse IDE. Install the Eclipse IDE from `https://www.eclipse.org/downloads/`. A direct link to the current installer executable on that page is <br/> `https://www.eclipse.org/downloads/download.php?file=/oomph/epp/2022-06/R/eclipse-inst-jre-win64.exe`

3. Once setup, Open Eclipse, and select the workspace `C:\DeMapMiner\workspace\`

The workspace should look like this:

![image](https://user-images.githubusercontent.com/17430034/180775091-6bc1120a-9577-4ab8-82a9-c43da1dffbf5.png)

**C. Generating the results.**

The results generation consists of the following three aspects, which can be executed one after another. <br/>
Note the results from the first step has already been populated in the database. <br/>
Also, the parameter sweepng has been cariied out. Thus, one can proceed directly to the Ranking evaluation. 

1. Generating the candidate reason sentences and messages. 
In this step. the heuristics approach is used to assign a score to sentences from messages of _accepted_ and _rejected_ PEPs.
Note that this task can take approximately 48 hours to complete.

2. Ranking evaluation  
The main ranking evaluation is within the rationaleMiner (project) -> rankingEvaluation (package) -> RankingEvaluation_Main.java class <br/>
Parameter sweeping is used to assign the optimum scores to each of the heuristics. In doing so, we also see whpch are the influential heuristics. 
In that class, the following tasks need to be performed one after another. All these tasks are needed for parameter sweeping. <br/> 
```
static Boolean removeDuplicates_Rank_TransferToNewTable = false, //we only remove duplicates once ever, ideally 
               weightAllocation = false,       //main processing 
               removeFeatures = false,		     //remove variables one by one from total score 
               trydifferentweights = false,    //set this if we want to check feature importance so above value would be automatically set for each variable; 
               assignFinalWeights = true;      //final scores are assigned
```

Note that this task will consider trying  different values for five most influential heuristics, and will take approximately five days to complete.
However, these tasks have already been carried out and the database has been populated with the results.

