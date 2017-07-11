---
title: "Starting your SQL Server's DevOps journey"
date: 2017-02-28 14:08:47
tags:
  - SSDT
  - MSBuild
  - Sqlpackage
  - Git
  - GitLab-CI
---
----
## DevOps Pipeline ##
The core idea of DevOps is to create a repeatable, reliable and incrementally improving process for taking software from concept to customer, enabling a constant flow of changes into production via an automated software production line.

The DevOps pipeline (or Continuous Delivery pipeline), in general, consists of three major stages. Each stage is aimed at verifying the quality of new features and prevent errors from continuing forward in the pipe. DevOps operation refers both application and server level. 

**Build :** Source code is transferred into a machine-readable package (binaries); New features implemented by the developers are integrated into the source code server on a continuous basis, built, and unit tested.

**Test :** The build package is tested to ensure it meets all desired system qualities, in aspects of functionality, security, performance and compliance.

**Deploy :** The deployment is automated, allowing for the reliable delivery of new functionality to users within minutes

This is my three steps advice to start your SQL Server DevOps journey :

##  Step 1 - Changing The Environment ##

Theoretically, developing a SQL Server database project is equal to developing any other software solution; It's only a matter of the developing tool you use. Software developers usually work in an offline editing mode - they write code, compile it, and only after running some tests, deploy it on a running machine.       

DBA's are used to SQL Server Management Studio as their developing tool. SSMS is an online editing tool, works on a live, running system. The first step to being taken to start building the DevOps pipeline is moving to an offline editing mode by changing our developing environment to Visual Studio SSDT.   

{% img pull-right col-md-4 /images/visual_studio.jpg %} [SQL Server Data Tools][2] is a database project development toolset, included in Visual Studio Comunity Edition since 2013, as part of the core product (not to be discussed here, the [Visual Studio SSDT shell](http://blog.nwcadence.com/sql-server-data-tools-clearing-up-the-confusion/) as a part of the SQL Server installation). The SSDT project system allows developers to have a fully representative source-code backed model of their database for offline development. 

## Step 2 - Under the hood of SSDT ##

Visual Studio SSDT is an IDE;  An integration of different tools and frameworks under a unified GUI. To build and automate the DevOps pipeline, it is necessary to undercover some of Visual Studio's command line tools:

* [** MSBuild.exe **][21] : Visual Studio IDE serializes T-SQL code files (.sql) into MSBuild XML file (.sqlproj). When running code in Visual Studio, MSBuild is executing the MSBuild file under the hood, outputting a database scheme package (DACPAC).  

*  [**MSTest**][22] : Visual Studio tool used to run tests.

* [** Sqlpackage.exe **][23]: Database project deployment and schema compare tool in  Visual Studio, is being executed by the Sqlpackage tool.

## Step 3 - SQL Server DevOps Pipeline ##

What has remained to complete the basic SQL Server DevOps pipeline is choosing the source code management tool and the automation tool to orchestrate the process.

* **Git :** Client side source code management tool. 

* **GitLab-CI :** GitHub's "enterprise edition" with Continuous Integration and Continuous Deployment capabilities; GitLab-CI is used as a source code server and Continuous Integration tool.

{% img /images/DevOpsPipeline.bmp %} Figure 1

Figure 1 describes a full possible SQL Server DevOps pipeline design, with the proper automation tools. These set of tools are my best choice; you can choose your own. 

---

## Coming next... ##
This is the first post in the series of "The DevOps pipeline" posts. In the next blog post, I will cover the in more depth the differences between SSMS and SSDT; Meanwhile, [follow this link][3] and take your first steps in SSDT.
[1]: https://devops.com/continuous-delivery-pipeline/
[2]: https://msdn.microsoft.com/en-us/library/hh272686(v=vs.103).aspx
[3]: https://www.youtube.com/watch?v=e6Z_MpXXnHU&t=3s
[4]: https://the.agilesql.club/blogs/Ed-Elliott/2016-01-05/What-Is-SSDT-Why-Should-I-Bother
[00]: https://devops.com/continuous-delivery-pipeline/
[21]: https://msdn.microsoft.com/en-us/library/dd393574.aspx#BKMK_CommandPrompt
[22]: https://msdn.microsoft.com/en-us/library/ms182489.aspx
[23]: https://msdn.microsoft.com/en-us/library/hh550080(v=vs.103).aspx
[31]: https://git-scm.com/
[32]: https://about.gitlab.com/gitlab-ci/