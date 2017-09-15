# ddnug-microservices
A repository for code related to my Sept. 19, 2017 talk at Dallas .NET User Group.

This is a microservices-based photo sharing application. Images can be uploaded via a Logic App, FTP or direct upload. A Web App provides a GUI to approve or delete sumbitted photos, and a Web API provides access to the approved photos.

## What's Here?
There are three .NET Framework 4.6.1 based Visual Studio projects in this repo:

**FileWatcherService** is a Windows service you can install on a virtual machine running IIS and FTP service. 

It will seek changed files in a given FTP directory, determine their type (XML or JPG), and add XML files to an Azure SQL Database, and images to Azure blob Storage, plus invoke a Service Bus message to create an image thumbnail.

**GalleryAPI** is a ASP.NET Web API 2 project that creates JSON of approved photos, which can be consumed by any external application

**Web UI** is an ASP.NET MVC application that allows you to upload images and moderate content.

There are additional folders in this repo:

**functions** contains the Azure Functions to resize, delete, and move images once approved from an upload Storage container to a different, permanent Storage container.

**Presentation** contains the slide deck for this presentation.

**Data** contains sample images and a sample XML file for the FTP file watcher.