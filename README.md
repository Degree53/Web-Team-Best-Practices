# Web Team Best Practices

*The following is a run down of best practices to use when working on projects in the web team. Bookmark, and use it as a reference. It will give you a strong idea of the way we work, and is there to help us work efficiently. That said, it is NOT set in stone. If you have any questions, improvements, suggestions, do speak up and hopefully we can improve it.*

## Table of Contents

1. [HTML](#html)
2. [CSS](#css)
3. [Javascript](#javascript)
4. [C#](#c#)
5. [Umbraco](#umbraco)
6. [SQL](#sql)
7. [Domain Urls](#domain-urls)
8. [Postman](#postman)
9. [Logging](#logging)
10. [Code Reviews](#code-reviews)
11. [Continuous Integration](#continuous-integration)
12. [Hosting](#hosting)

## HTML

* Semantics

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

## Umbraco

Generally we try to keep the same structure for all of our projects where possible. This ensures that if you need to switch projects, or start a new one, you can recognise what's going on more easily, and already be familiar with a project and work more efficiently.

* New Projects
    * Fork the template project. It is loaded with code samples of things we use regularly.
    * LastPass - Make logins for different environments as soon as they are setup, even if they share the same password.
* Ensure you have the [Middleware Nuget repo](https://sites.google.com/a/degree53.com/knowledge-base/technical/middleware/nuget-repository) added to your Visual Studio
* [Editors Manual](https://our.umbraco.org/projects/website-utilities/umbraco-7-editors-manual/) - The Umbraco manual. Usually, this is a starting point to modify and customise for any clients. See a project manager for any sample/custom ones we have produced.
* Custom Property Editors
* Custom Grid Editors
* Controllers - Use appropriately.
    * RenderViewController
    * SurfaceController
    * UmbracoApiController
    * UmbracoAuthorizedApiController
* [ORM](http://www.toptensoftware.com/petapoco/) - There is an ORM built into Umbraco, PetaPoco. Sometimes this may be easier than creating new tables and writing custom code for CRUD operations, but be aware of any performance hits.

## SQL

> For your information

* Naming Conventions for DB's
    * Dev - {PascalCaseSitename}Dev
    * Test - {PascalCaseSitename}Test
    * UAT - {PascalCaseSitename}UAT

## Domain Urls

Setting URL's is good practice. If we didn't do it, we'd have issues for example if we were to migrate our sites to another hosting provider.

* Setting urls for environments (See Warren for assistance if it's not possible to do yourself)
    * Dev - http://{sitename-lowercase-hyphenated}-dev.degree53.com
    * Test - http://{sitename-lowercase-hyphenated}-test.degree53.com
    * UAT - http://{sitename-lowercase-hyphenated}-uat.degree53.com

## Postman

* Shared Degree 53 Dev Account (*degreefiftythree.dev@gmail.com*, see LastPass)
* There should be environament variables that you can use to switch between different environments, eg. {{dev}}, {{test}}, {{UAT}}. Use these when adding any API calls.

## Logging

* Log4Net

```
private static readonly ILog Log = LogManager.GetLogger(MethodBase.GetCurrentMethod().DeclaringType);
```

* [Diplo Trace Log Viewer](https://our.umbraco.org/projects/developer-tools/diplo-trace-log-viewer/) - Add this to your umbraco installation if it isn't there already (it should be in the template project), in order to view logs more easily! If you're unsure whether or not to add it, ask someone!

## Code Reviews

* *WIP*

## Continuous Integration

* [Git Workflow](https://sites.google.com/a/degree53.com/knowledge-base/technical/front-end/git-workflow)
* TeamCity
    * Errors - Read build log errors. They are your best friend when trying to resolve build issues.

## Hosting

* Azure - Log into the [Portal](http://portal.azure.com) using your own Degree 53 account. It should be setup with the correct permissions to access what you need. If you don't have the correct permissions, see Bav.