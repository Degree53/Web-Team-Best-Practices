# Web Team Best Practices

*The following is a run down of best practices to use when working on projects in the web team. Bookmark, and use it as a reference. It will give you a strong idea of the way we work, and is there to help us work efficiently. That said, it is NOT set in stone. If you have any questions, improvements, suggestions, do speak up and hopefully we can improve it.*

## Table of Contents

0. [Prerequisites](#prerequisites)
0. [HTML](#html)
0. [CSS](#css)
0. [Javascript](#javascript)
0. [C#](#c#)
0. [Umbraco](#umbraco)
0. [SQL](#sql)
0. [Container Apps](#container-apps)
0. [Domain Urls](#domain-urls)
0. [Email](#email)
0. [Postman](#postman)
0. [Logging](#logging)
0. [Code Reviews](#code-reviews)
0. [Continuous Integration](#continuous-integration)
0. [Hosting](#hosting)
0. [Tools](#tools)
0. [Tracking](#tracking)

## Prerequisites

* [Middleware Nuget Repo](https://sites.google.com/a/degree53.com/knowledge-base/technical/middleware/nuget-repository)  - Ensure you have the 'Middleware Nuget Repo' added to your instance of Visual Studio.
* Running in Administrator mode for projects - You may not wish too, and this fix helps - http://stackoverflow.com/questions/12859891/error-unable-to-access-the-iis-metabase

## HTML

* Semantics - We should be aware of the semantics, using elements appropriately. It's important, and there isn't any reason why we shouldn't know about them. Have a google yourself, below is an article that may be of us to you.
    * [https://codepen.io/mi-lee/post/an-overview-of-html5-semantics](https://codepen.io/mi-lee/post/an-overview-of-html5-semantics)
    * [Google's Structured Data Testing Tool](https://search.google.com/structured-data/testing-tool) - Google Tool to test microdata.
    * [SEO](SEO.md)

## CSS

Take the time to read the Degree 53 CSS Style Guide. The style guide is used throughout the company by the web and front-end teams. Adhere to it as much as you can in our projects.

* [Degree 53 CSS Style Guide](https://github.com/Degree53/css)

## Javascript

Take the time to read the Degree 53 Javascript Style Guide. The style guide is used throughout the company by the web and front-end teams. Adhere to it as much as you can in our projects.

* [Degree 53 Javascript Style Guide](https://github.com/Degree53/javascript)

## C#

We follow the Microsoft C# Coding and Naming Conventions. Take a look, and ADHERE to them.

* [Coding Conventions](https://msdn.microsoft.com/en-gb/library/ff926074.aspx)
* [Naming Conventions](https://msdn.microsoft.com/en-us/library/ms229045(v=vs.110).aspx)
* Version Numbers - *TBC*

## Umbraco

Generally we try to keep the same structure for all of our projects where possible. This ensures that if you need to switch projects, or start a new one, you can recognise what's going on more easily, and already be familiar with a project and work more efficiently.

* [Umbraco](UMBRACO.md)

## SQL

> For your information

For each database/site you are building a database for in Azure, [create an individual account with the required permissions](https://sites.google.com/a/degree53.com/knowledge-base/it-helpdesk/sql-azure). Do NOT use the master account to connect to the database, either for the website, or in SQL Server Management Studio. Too much can go wrong.

* Naming Conventions for DB's
    * Dev - {PascalCaseSitename}Dev
    * Test - {PascalCaseSitename}Test
    * UAT - {PascalCaseSitename}UAT
    * Live/Production - {PascalCaseSitename}Prod

Most of the time you will probably be just fine using Umbraco's content service, or other means of displaying data, but there will be times when you need to directly work with the database, such as creating tables, views and stored procedures.

Firstly, really plan what you are going to do. Think about the project, and why you want to do it a certain way. Document it. Get it checked by someone.

Saving the scripts - *TBC*

## Container Apps

* IPV6 Checking
    * [Apple - Supporting IPv6 DNS64/NAT64 Networks](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html)

## Domain Urls

Setting URL's is good practice. If we didn't do it, we'd have issues for example if we were to migrate our sites to another hosting provider.

* Setting url's for environments (See Warren for assistance if it's not possible to do yourself)
    * Dev - http://{sitename-lowercase-hyphenated}-dev.degree53.com
    * Test - http://{sitename-lowercase-hyphenated}-test.degree53.com
    * UAT - http://{sitename-lowercase-hyphenated}-uat.degree53.com

## Email

* Sendgrid - We have a Degree 53 account that you can use to send emails in your code using SendGrid.
* You can use smtp4dev locally to quickly fire off some emails and check things are working.

## Postman

* Shared Degree 53 Dev Account (*degreefiftythree.dev@gmail.com*, see LastPass)
* There should be environament variables that you can use to switch between different environments, eg. {{dev}}, {{test}}, {{uat}}. Use these when adding any API calls.

## Logging

* Log4Net

```
private static readonly ILog _log = LogManager.GetLogger(MethodBase.GetCurrentMethod().DeclaringType);
```

* [Diplo Trace Log Viewer](https://our.umbraco.org/projects/developer-tools/diplo-trace-log-viewer/) - Add this to your umbraco installation if it isn't there already (it should be in the template project), in order to view logs more easily! If you're unsure whether or not to add it, ask someone!

## Code Reviews

* *TBC*

## Continuous Integration

* [Git Workflow](https://sites.google.com/a/degree53.com/knowledge-base/technical/front-end/git-workflow)
* [TeamCity](https://sites.google.com/a/degree53.com/knowledge-base/technical/continous-integration/teamcity)
    * Errors - Read build log errors. They are your best friend when trying to resolve build issues.
    * Version Numbers
    * Release Tags

## Hosting

* Azure - Log into the [Portal](http://portal.azure.com) using your own Degree 53 account. It should be setup with the correct permissions to access what you need. If you don't have the correct permissions, see Bav.

## Tools

* [https://search.google.com/search-console/mobile-friendly](https://search.google.com/search-console/mobile-friendly)
* Visual Studio Productivity Power Tools - Install this and it will make your life easier. More importantly, it can enforce tabs/spaces, and few other things in your code.
* [SQL Server Migration Wizard](https://blogs.msdn.microsoft.com/prasanna/2015/04/13/migrating-sql-server-on-premise-db-to-sql-azure-using-sql-server-migration-wizard/) - Invaluable when migrating databases between environments, handling issues like DB versions with ease.
    * [Download](https://sqlazuremw.codeplex.com/releases/view/32334)

## Tracking

* Google Tag Manager - Ideally we should add Google Analytics via Google Tag Manager. It means, we only need to install GTM, and things can be added when required, without affecting development.
    * [Quick Start Guide](https://developers.google.com/tag-manager/quickstart) - Tag Manager Code placement
    * https://support.google.com/analytics/answer/6164470
* Google Analytics
