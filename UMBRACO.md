# Umbraco

*The following is a run down of best practices to use when working on umbraco projects in the web team. It will give you a strong idea of the way we work, and is there to help us work efficiently. That said, it is NOT set in stone. If you have any questions, improvements, suggestions, do speak up and hopefully we can improve it.*

*Generally we try to keep the same structure for all of our projects where possible. This ensures that if you need to switch projects, or start a new one, you can recognise what's going on more easily, and already be familiar with a project and work more efficiently.*

## Table of Contents

1. [New Projects](#new-projects)
2. [Editors Manual](#editors-manual)
3. [Controllers](#controllers)
4. [Data Access](#data-access)
5. [Custom Editors](#custom-editors)
6. [Custom Sections](#custom-sections)
7. [Logging](#logging)
8. [Reading](#reading)
9. [Performance](#performance)

## New Projects

* Fork the template project (*TBC*). It is loaded with code samples of things we use regularly.
* LastPass - Make logins for different environments as soon as they are setup, even if they share the same password.

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

## Reading

Useful articles, give these a read to make you aware of any features that can make your life easier and write better code.

* [Common Pitfalls](https://our.umbraco.org/documentation/Reference/Common-Pitfalls/) - The Umbraco docs are pretty good in general, this article is pretty good for some general tips and best practices.
* [Official Umbraco C# API documentation](https://our.umbraco.org/apidocs/csharp/)

## Performance

* When running Umbraco on Azure, it works slightly differently to how it does locally. There are two parts, the file system, and the web worker. The web worker is what you actually connect to in your browser, and where the site is run from. The file system is where static files, indexes, etc. are loaded from and used. The web worker will occasionally be unloaded, and reloaded into a new web worker, which will cause the site to 'restart', causing it to reload the content cache again.
    * Copy the content cache file to the web worker memory, in 'Config/umbracoSettings.config'.
```
<!-- Update in-memory cache if XML file is changed -->
<XmlContentCheckForDiskChanges>True</XmlContentCheckForDiskChanges>
```
