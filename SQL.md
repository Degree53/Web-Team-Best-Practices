# SQL

*The following is a run down of best practices to use when working with SQL databases in the web team.*

*Generally we try to keep the same structure for all of our projects where possible. This ensures that if you need to switch projects, or start a new one, you can recognise what's going on more easily, and already be familiar with a project and work more efficiently.*

## Local DB

To install a local instance of SQL Server, install [SQL Server Express Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

## Azure

For each database/site you are building a database for in Azure, [create an individual account with the required permissions](https://sites.google.com/a/degree53.com/knowledge-base/it-helpdesk/sql-azure). Do NOT use the master account to connect to the database, either for the website, or in SQL Server Management Studio. Too much can go wrong.

* Naming Conventions for DB's
    * Dev - {PascalCaseSitename}Dev
    * Test - {PascalCaseSitename}Test
    * UAT - {PascalCaseSitename}UAT
    * Live/Production - {PascalCaseSitename}Prod

Most of the time you will probably be just fine using Umbraco's content service, or other means of displaying data, but there will be times when you need to directly work with the database, such as creating tables, views and stored procedures.

Firstly, really plan what you are going to do. Think about the project, and why you want to do it a certain way. Document it. Get it checked by someone.

Saving the scripts - *TBC*

## Drop a database
```
DROP DATABASE DBName
GO
```

## Copy a database
```
CREATE DATABASE DestinationDatabaseName
     AS COPY OF [SourceDatabaseName]
GO
```

## Exporting Databases

If you need to convert an SDF DB file to a SQL server DB, use CompactView and export the DB, then run the script in the newly created one.

The [Migration Wizard](https://github.com/adragoset/SQLAzureMigration) tool is still the best in my opinion, however it appears to have been superceded by the [Data Migration Assistant](https://docs.microsoft.com/en-us/sql/dma/dma-overview?view=sql-server-2017).