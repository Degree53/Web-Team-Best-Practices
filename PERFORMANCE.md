# Performance

*The following is a collection of tips and pitfalls we can look at when improving performance of a web app/site. The important thing to remember is to keep this in mind as you are going along. Shoehorning it in at the end is sometimes necessary, but it means you'll probably end up doing work twice, do it right the first time.*

## Table of Contents

0. [Azure](#azure)
0. [Umbraco](#umbraco)

## Azure
* This will improve the speed at which static files are served from the azure server. If this doesn't run locally, you can add it to your config transforms.
    ```
    <system.webServer>
    <serverRuntime enabled="true" frequentHitThreshold="1" frequentHitTimePeriod="00:00:20" />
    ...
    </system.webServer>
    ```

* Enable the 'Always On' setting. This can be found in Application Settings in the App Service settings. This will prevent the site from 'going to sleep', acting as a keep alive function.

## Umbraco

* [Umbraco Performance](UMBRACO.md#performance)
