# Building a Web Service in C# 

Summary: We are going to set up a simple web service coded in C# using .Net Core.  To accomplish this we’ll learn some C# fundamentals, then use .Net’s scaffolding to create a web api and development server we can run.  We will interact with this web api using a simple angular app.

## Installed Prerequisites:
- Node & npm 
    - https://nodejs.org/en/
-- npm install npm@latest -g
- Angular CLI
-.Net (What version? How?)
- VS Code or similar editor
-- With https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp

# C#
1. According to Wikipedia
 - C#[b] (pronounced C sharp) is a general-purpose, multi-paradigm programming language encompassing strong typing, lexically scoped, imperative, declarative, functional, generic, object-oriented (class-based), and component-oriented programming disciplines.
 -- General purpose language
 -- Strongly Typed
Some exceptions…
Object Oriented
Some exceptions…
History, Open Source status
Versions
Future
Coding Environments
Visual Studio
The primary IDE from MS
Tends to be very large and expensive
Has some of the best tools and is used in most workplaces
Rider
Made by Jetbrains, who makes Resharper
Cheaper, but not cheap
Has great reviews 
VS Code
Free
Cross Platform
Still made by MS!
Our choice for today
Other tools I will use today
Command prompt/powershell
Postman
LinqPad
Git 
Tortoisegit
Github
.Net Core
What is it vs. What it isn’t
Where it can be deployed
ASP.Net Core
Exercise
Every front end needs services that connect it to the backend/data storage
Front end will be a simple provided Angular App
Get this from Github
Run from command line
Our back end will be returning static data rather than accessing a database at this time
Advanced, perhaps point to an AWS dynamodb service?
Get Partial C# project with layout from GitHub
dotnet new webapi -o TodoApi
Implement a Get Operation
Do code
Spin up service from command line
Demonstrate working with postman
Connect with angular app
Implement Post Operation
Do Code
Spin up service from command line
Demonstrate working code with postman
Connect with angular app
What we learned from this
Simple process that could be dockerized provides back end for front end application
References
https://docs.microsoft.com/en-us/aspnet/core/getting-started/?view=aspnetcore-2.2&tabs=windows
https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-2.2&tabs=visual-studio
https://www.sitepoint.com/angular-2-tutorial/  (THIS IS OLD AVOID IT)
https://en.wikipedia.org/wiki/C_Sharp_(programming_language)
Important Topics not covered
In depth HTTP 
Object Oriented / Inheritance / Interfaces
Unit Testing
IL / .Net (what makes C# into machine code)
Dependency Injection
Error Handling
Async/Await, Tasks, concurrency
IIS & other web servers
Nuget
Angular (in any way)
