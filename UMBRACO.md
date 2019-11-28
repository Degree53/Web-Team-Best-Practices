# Umbraco

*The following is a run down of best practices to use when working on umbraco projects in the web team. It will give you a strong idea of the way we work, and is there to help us work efficiently. That said, it is NOT set in stone. If you have any questions, improvements, suggestions, do speak up and hopefully we can improve it.*

*Generally we try to keep the same structure for all of our projects where possible. This ensures that if you need to switch projects, or start a new one, you can recognise what's going on more easily, and already be familiar with a project and work more efficiently.*

Read the new Project section to begin with.

## Table of Contents

1. [New Projects](#new-projects)
1. [Editors Manual](#editors-manual)
1. [Controllers](#controllers)
1. [Data Access](#data-access)
1. [Custom Editors](#custom-editors)
1. [Custom Sections](#custom-sections)
1. [Logging](#logging)
1. [Debugging](#debugging)
1. [Reading](#reading)
1. [Performance](#performance)
1. [Patches](#patches)
1. [Release Checklist](#release-checklist)

## New Projects

* Fork the template project (*TBC*). It is loaded with code samples of things we use regularly.
* LastPass - Make logins for different environments as soon as they are setup, even if they share the same password.
* [Running Umbraco on Azure Web Apps](https://our.umbraco.com/documentation/Getting-Started/Setup/Server-Setup/azure-web-apps)

## Editors Manual

* [Editors Manual](https://our.umbraco.org/projects/website-utilities/umbraco-7-editors-manual/) - The Umbraco manual. Usually, this is a starting point to modify and customise for any clients. See a project manager for any sample/custom ones we have produced.

## Controllers

* Controllers - Use appropriately.
    * [RenderMvcController](https://our.umbraco.org/documentation/reference/routing/custom-controllers)
    * [SurfaceController](https://our.umbraco.org/documentation/reference/routing/surface-controllers)
    * [UmbracoApiController](https://our.umbraco.org/documentation/reference/routing/WebApi/)
    * [UmbracoAuthorizedApiController](https://our.umbraco.org/documentation/reference/routing/Authorized/)

## Data Access

* [ORM](http://www.toptensoftware.com/petapoco/) - There is an ORM built into Umbraco, PetaPoco. Sometimes this may be easier than creating new tables and writing custom code for CRUD operations, but be aware of any performance hits.

## Custom Editors

* Custom Property Editors
    * [Creating a Property Editor](https://our.umbraco.org/documentation/tutorials/Creating-a-Property-Editor/)
    * [Data Types](https://our.umbraco.org/forum/developers/extending-umbraco/46183-Creating-a-property-editor-in-Umbraco-7) - Use 'valueType: "JSON"' to avoid data size storing issues.
* Custom Grid Editors

## Custom Sections

* [http://skrift.io/articles/archive/sections-and-trees-in-umbraco-7/](http://skrift.io/articles/archive/sections-and-trees-in-umbraco-7/)

## Logging

* Log4Net

```
private static readonly ILog Log = LogManager.GetLogger(MethodBase.GetCurrentMethod().DeclaringType);
```

* [Diplo Trace Log Viewer](https://our.umbraco.org/projects/developer-tools/diplo-trace-log-viewer/) - Add this to your umbraco installation if it isn't there already (it should be in the template project), in order to view logs more easily! If you're unsure whether or not to add it, ask someone!

## Debugging

Add this to any URL to get a stack trace in your browser. It'll also tell you where bottlenecks are, and even SQL queries that are slowing things down.

```
?umbDebug=true&umbDebugShowTrace=true
```

## Reading

Useful articles, give these a read to make you aware of any features that can make your life easier and write better code.

* [Common Pitfalls](https://our.umbraco.org/documentation/Reference/Common-Pitfalls/) - The Umbraco docs are pretty good in general, this article is pretty good for some general tips and best practices.
* [Official Umbraco C# API documentation](https://our.umbraco.org/apidocs/csharp/)
* [Running Umbraco on Azure Web Apps](https://our.umbraco.org/documentation/Getting-Started/Setup/Server-Setup/azure-web-apps)

## Performance

* When running Umbraco on Azure, it works slightly differently to how it does locally. There are two parts, the file system, and the web worker. The web worker is what you actually connect to in your browser, and where the site is run from. The file system is where static files, indexes, etc. are loaded from and used. The web worker will occasionally be unloaded, and reloaded into a new web worker, which will cause the site to 'restart', causing it to reload the content cache again.
    * Copy the content cache file to the web worker memory, in 'Config/umbracoSettings.config'.
```
<!-- Update in-memory cache if XML file is changed -->
<XmlContentCheckForDiskChanges>True</XmlContentCheckForDiskChanges>
```
## Patches

* [Security Patch](https://umbraco.com/blog/security-advisory-security-patch-ready-on-the-20th-of-september/)

## Load Balanced Setup

* Follow the steps outlined here:
	* [Common load balancing setup information] (https://our.umbraco.com/documentation/getting-started/setup/server-setup/load-balancing/#common-load-balancing-setup-information)
	* [Examine Directory Factory Options] (https://our.umbraco.com/documentation/getting-started/setup/server-setup/load-balancing/file-system-replication#examine-directory-factory-options)
	* [Explicit Master Scheduling Server] (https://our.umbraco.com/documentation/getting-started/setup/server-setup/load-balancing/flexible-advanced#explicit-master-scheduling-server)
* Add app setting for load balancing role
* Set server registrar on application start based on load balancing role
* Install UmbracoFileSystemProviders package for storing media in Azure blob storage
* Release config for FileSystemProviders with storage account connection string
* Setup a new Azure app service to host the master Umbraco instance
* Redirect rule for master Umbraco site with the following exclusions:
	*umbraco
	*umbraco/api
	*umbraco/backoffice
	*umbraco/restservices
* Clear indexes (including any write.lock files) from slave server (may require app service to be stopped)

## Scheduled Publishing

* Ensure security protocol type is set to TLS12 on application start
* Ensure there is no redirect affecting `umbraco/restservices` (required for background tasks such as scheduled publishing)

## Release Checklist

Things to look out for when upgrading Umbraco, or doing a large release. These things are often overlooked, so keep a lookout.

* Umbraco Forms
	* Copy Data folder in UmbracoForms plugin folder
	* Ensure UmbracoForms license files are included in the solution and are set to copy to the bin
* Copy media folder
* Import SQL changes with uSync
* Rebuild Examine indexes
* Regenerate models
* Clear App_Data/TEMP/ClientDependency folder

* Configs - These include things like Dashboard (which can affect what you see in the backoffice), performance settings, etc.
* If upgrading, content pickers can change, and no longer work, often requiring code changes in views.
* Use deployment slots for big upgrades - don't forget to copy media, form files, licenses, etc. Azure will handle SSL, custom domains, etc.
    * Test the newly swapped in site, with the old one if using multiple databases to check that everything has copied over ok.