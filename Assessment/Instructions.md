# Final Assessment &mdash; Administering a SQL Database Infrastructure
*13 May 2022*
## Assessment objectives
Any candidate achieving a passing grade has demonstrated competence in the following objectives:
- Backup SQL Server databases
- Restore SQL Server databases
- Managing SQL Server using PowerShell
- Trace access to SQL Server
- Monitor SQL Server infrastructure

## Please Note:
1. This assessment is *performance-based*, which means you must perform certain tasks, the results of which will determine whether you pass/fail.
1. This assessment is *open-book*, which means you may use ***any*** reference materials in performing the tasks required. This is meant to simulate the *real world*.
1. This assessment is *time-based*, which means you must accomplish sufficient tasks to accumulate sufficient points to warrant a passing score.
## Prepare the assessment environment
If you have any problems with the following tasks, please contact your instructor.
- [ ] Ensure the lab virtual machine is started
- [ ] Ensure there is ***at least*** 4 hours of remaining lab time  (preferably more)
- [ ] Logon to the 20764C-MIA-SQL computer as `Student`
- [ ] Open *SQL Server Management Studio* `(SSMS)` and logon on to the `DEFAULT` instance of SQL Server Database Engine
- [ ] Breathe :flushed:

## Tasks to accomplish
1. Create and populate a database ([Task 1](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-1--create-and-populate-a-database)) `20 points`
1. Backup the new database ([Task 2](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-2--backup-a-database)) `20 points`
1. Modify the database ([Task 3](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-3--modify-a-database)) `20 points`
1. Restore the database ([Task 4](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-4--restore-a-database)) `20 points`
1. Create a database maintenance plan ([Task 5](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-5--create-a-database-maintenance-plan)) `40 points`
1. Perform a *trace* to identify long-running queries ([Task 6](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-6--perform-a-trace)) `40 points`
1. Create a performance monitoring plan using out-of-the-box tools ([Task 7](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-7--monitor-sql-server)) `40 points`
## Instructions
- [X] The assessment must be completed within `4 hours`
- [X] There are `200 points` available over 7 tasks&mdash;passing score is `160 points` (80%)
- [X] Tasks may be undertaken in any order (some cannot be done before others&mdash;most tasks depend on the assessment database having been created)
- [X] Several tasks have code to run in SSMS&mdash;leave the results window open for the assessment observation
  >  - [X] Scripts may be run more than once safely and will not affect the assessment observation
- [X] Disconnect from the Teams call while doing the assessment
    > - [X] Reconnect when you want [some of] your work assessed
    > - [X] Your instructor will monitor your labs during the assessment
- [X] :alarm_clock: Manage your time&mdash;assessment observations must be completed within `4 hours` of starting the assessment

## Task 1 &mdash; Create and populate a database
> 20 points
### Overview
:warning: Do this task first as most of the other tasks require the database to have been created!

This task is meant to simulate an application installed that requires the creation of a SQL database. For simplicity, a script is provided that can be downloaded from an Azure storage account that will create and populate the database.
### Resources
Download the following script and open it in SSMS
- [Create Database Script](https://linton.blob.core.windows.net/public/Create%20and%20Populate%20Database.sql)
> The lab VM only has Internet Explorer installed, which can download the script; choose *Open* in the prompt at the bottom of the Internet Explorer browser window. This will open the script in SSMS for you.

### Instructions
1. Open the `Create and populate database.sql` script in SSMS
1. Run the script
    1. Keep the *Results* window open for the assessment observation
> If you run the script more than once, you will get an error, but the *Results* tab should show the results correctly.

Alternatively, you can run the following query
```SQL
USE assessment
SELECT COUNT(1) AS [N], SUM(price) AS [Sigma] FROM assessment.prices;
```
### Success Criteria `20 points`
- [ ] `assessment` database observed&mdash;`10 points`
- [ ] Query results show similar to this screenshot&mdash;`10 points`

![Task 1 Results Window](https://github.com/charliebravotango/Linton2022/blob/main/Artefacts/Task1results.png)
## Task 2 &mdash; Backup a database
> 20 points (maximum)&mdash;`60 points` available

### Overview
This task is meant to simulate a requirement to take an *ad hoc* backup of the database to the server's filesystem. 
### Resources
There is no script for this task.
- [ ] Create a folder to store the backups, for instance `C:\BACKUP`

### Instructions
#### SMSS method
1. Use *Object Explorer* to take a backup of the database
1. Close the dialog box(es); your instructor will ask you to demonstrate the settings you used to take the backup
#### Transact-SQL method
1. Use the `BACKUP DATABASE` T-SQL command to back up the database
1. Leave the query window (with its results) open for your instructor to observe when assessing this task

:notebook: A helpful example, [link](https://docs.microsoft.com/en-us/sql/t-sql/statements/backup-transact-sql?view=sql-server-ver15#backing_up_db) to `BACKUP DATABASE` *Books Online* example.
#### PowerShell method [bonus points]
1. Use the `BACKUP-SQLDATABASE` PowerShell commandlet
1. Leave the PowerShell window open for assessment observation 

:notebook: [Link](https://docs.microsoft.com/en-us/powershell/module/sqlserver/backup-sqldatabase?view=sqlserver-ps#examples) to helpful examples from the PowerShell documentation.

:warning: This method gains double points!
### Success Criteria `20 points`
- [ ] Command to backup database observed&mdash;`10 points`
- [ ] Backup file observed with appropriate timestamp&mdash;`10 points`

:warning: If you used the *Object Explorer* method to take the backup, your instructor will ask you to demonstrate the configuration of the dialog box(es) you used without having to perform the backup again.
## Task 3 &mdash; Modify a database
> 20 points

### Overview
This task is meant to simulate application activity in the database. For simplicity, a script is provided that can be downloaded from an Azure storage account that will modify the database's data.
### Resources
Download the following script and open it in SSMS
- [Simulate Activity Script](https://linton.blob.core.windows.net/public/Simulate%20Activity.sql)
> The lab VM only has Internet Explorer installed, which can download the script; choose *Open* in the prompt at the bottom of the Internet Explorer browser window. This will open the script in SSMS for you.
### Instructions
1. Open the `Simulate Activity.sql` script in SSMS
1. Run the script

Alternatively you can type the following script into SSMS directly and run it.
```SQL
UPDATE assessment.dbo.prices SET price = id + 200;
SELECT COUNT(1) AS [N], SUM(price) AS [Sigma] FROM assessment.prices;
```
:warning: It is safe to run the script above as many times as you like, the results will always be the same!
### Success Criteria `20 points`
- [ ] Script execution results match the following screenshot&mdash;`20 points`

![Task 2 Results Window](https://github.com/charliebravotango/Linton2022/blob/main/Artefacts/Task2Results.png)
## Task 4 &mdash; Restore a database
> 20 points (maximum)&mdash;`80 points` available
### Overview
This task is meant to simulate recovering from a disaster. However, for simplicity and to prevent overwriting the database (which would break the ability to perform the tasks in any order) we will restore a previous backup, such as performed in [Task 2 &mdash; Backup a database](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-2--backup-a-database), to a ***new*** database.
### Resources
This task requires that a database backup has been performed from another task, such as [Task 2 &mdash; Backup a database](https://github.com/charliebravotango/Linton2022/blob/main/Assessment/Instructions.md#task-2--backup-a-database).
- [ ] Database backup

### Instructions
#### SSMS method
1. Use *Object Explorer* to restore a database from a previously-taken backup
1. Restore to a new database, which will require a unique name, such as `assessment-restored`
1. Close any dialog boxes once completed&mdash;your instructor will ask you to demonstrate the settings used when performing assessment observation
#### Transact-SQL method
1. Use the `RESTORE DATABASE` command to restore a database from a previously-taken backup
1. Restore to a new database, which will require a unique name, such as `assessment-restored`
1. Leave the query window (with its results) open for your instructor to observe when assessing this task

:notebook: A helpful example [link](https://docs.microsoft.com/en-us/sql/t-sql/statements/restore-statements-transact-sql?view=sql-server-ver15#restoring_db_n_move_files "SQL Server Books online") to *Books Online* documentation.
#### PowerShell method [bonus points]
1. Use the `RESTORE-SQLBACKUP` PowerShell comandlet
1. Leave the PowerShell window open for assessment observation

:notebook: [Link](https://docs.microsoft.com/en-us/powershell/module/sqlserver/restore-sqldatabase?view=sqlserver-ps#examples "PowerShell Documentation") to examples from the PowerShell documentation.

:warning: This method gains double points!
### Success Criteria `40 points`
- [ ] Command to restore the backup observed&mdash;`10 points`
- [ ] Restore operation successful&mdash;`10 points`
- [ ] New database observed&mdash;`10 points`
- [ ] New database files have unique names&mdash;`10 points`

:warning: If you used the *Object Explorer* method to perform the restore, your instructor will ask you to demonstrate the configuration of the dialog box(es) you used without having to perform the restore again.
## Task 5 &mdash; Create a database maintenance plan
> 40 points (maximum) &mdash; `50 points` available
### Overview
Regular database maintenance is important to keep the database (as opposed to the database *server*) running efficiently. This normally includes index maintenance and regular backups.

:warning: This task has no prerequisites and may be done at any time and on any database including system databases such as `master`.
### Resources
This task has no specific resources required.

However, bookmark [Brent Ozar's Scripts](https://www.brentozar.com/first-aid/ "Free SQL Server Maintenance Scripts") for future reading and download.
### Instructions
Your maintenance plan(s) should take care of [at least] the following operations:
- Database integrity
- Statistics updates
- Index fragmentation
- Database backups (full, differential, *and* transaction log (where appropriate))
- Cleanup

#### Maintenance Plan method
1. Use *Object Explorer* to create one or more *Maintenance Plan(s)*
1. Use an appropriate name for the plan(s)
1. Use an appropriate schedule for the plan(s)
1. Execute the plan at least once to check it runs without error

:warning: Be prepared to explain your rationale for the configuration(s) you have used.
#### SQL Server Agent Job method
Use *Transact-SQL* as the job step type&mdash;you *could* use PowerShell or SSIS for these tasks, but *Transact-SQL* is more appropriate in this context.
1. Verify the SQL Server Agent is set to start automatically when the database engine starts
1. Verify the SQL Server Agent is running
1. Create one or more jobs, with one or more steps, to perform the operations listed above
1. Use appropriate names for the jobs and job steps
1. Use appropriate schedule(s) for the jobs
1. Execute the job(s) at least once to check they run without error

:warning: Be prepared to explain your rationale for the configuration(s) you have used.
### Success Criteria `40 points`
In this context *Maintenance Plan* and *SQL Server Agent Job* are referred to simply as *'plan'*.
- [ ] One or more plans created&mdash;`10 points`
- [ ] Plan has an appropriate name&mdash;`10 points`
- [ ] Plan has an appropriate schedule&mdash;`10 points`
- [ ] Plan(s) perform all 7 operations appropriately&mdash;`10 points`
- [ ] Plan(s) execute without error when invoked manually&mdash;`10 points`

:star2: A maximum of `40 points` will be allocated even if more than 40 points are awarded.
## Task 6 &mdash; Perform a trace
> 40 points
### Overview
Being able to identify what is going on inside SQL Server is a specialised task, that requires years of experience; this task gets you to demonstrate that you have the basics of knowledge of the tools available *out-of-the-box* to look forensically at activity inside the database engine.

Placeholder
## Task 7 &mdash; Monitor SQL Server
> 40 points
### Overview
"The database is very slow today!" is a very common complaint from end-users. Being able to identify 
Placeholder