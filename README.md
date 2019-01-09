# SqlExpress-Agent-On-Windows

I was working with a project that requires to run jobs in the database, but I found out the SQLEXPRESS does not come with this feature. This repo is intended to show how to simulate the SQL Agent Server in MSSQLServer using SQLEXPRESS.

## Getting Started

These instructions will get you through a series of steps so you can have a simulated agent running a task on your SQLEXPRESS database.

### Prerequisites

* Microsoft Management Console and be an Administrator
* SQLEXPRESS installed
* Tables and Stored Procedure created in the database
* Text editor

### Installing

* You will need to find the Microsoft Management Console, right click on the Computer Icon in your desktop and select Manage.
* Create a task using this [tutorial](https://www.dummies.com/computers/pcs/how-to-create-a-task-to-run-a-program-in-windows-task-scheduler/)
* The script to run should be a bat file like this one

```
    SQLCMD -S .\SQLEXPRESS -U user -P password -i sql_file.sql -h -1 > auto_gerenerated_output_file.txt
    EXIT
```

This is a command connecting the local computer (`.\`) database (`SQLEXPRESS`) using the user **user** and password **password** and executing the sql file **sql_file.sql** and generating the output file **auto_gerenerated_output_file.txt**. This file will ve overwritten every time the task is executed.

* and last but not least, the sql command should be like this one
```
    USE DatabaseName;

    PRINT 'Printing a List'
    EXEC dbo.Getlist;

    PRINT 'Running a SP'
    EXEC dbo.MyStoredProcedure;

    GO
```

This will run these two stored procedures

### Troubleshooting

* In case you have any issue running the task read this StackOverflow [answer](https://stackoverflow.com/questions/18370547/windows-scheduled-task-succeeds-but-returns-result-0x1)

### Other options

For other options click on this [link](https://stackoverflow.com/questions/3788583/automate-a-sql-query-to-run-every-month/3789024#3789024)
