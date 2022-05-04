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
    1. Keep the *Results* window open for the assessment
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

Placeholder
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
> 20 points

Placeholder&mdash;Simulates recovering from a disaster
## Task 5 &mdash; Create a database maintenance plan
> 40 points

Placeholder
## Task 6 &mdash; Perform a trace
> 40 points

Placeholder
## Task 7 &mdash; Monitor SQL Server
> 40 points

Placeholder