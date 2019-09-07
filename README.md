# Building a Web Service in C# 

Summary: We are going to set up a simple web service coded in C# using .Net Core.  To accomplish this we’ll learn some C# fundamentals, then use .Net’s scaffolding to create a web api and development server we can run.  We will interact with this web api using a simple angular app.

## Installed Prerequisites:
- Node & npm 
    - https://nodejs.org/en/
    - npm install npm@latest -g
- Angular CLI
    - npm install -g @angular/cli
- .Net (What version? How?)
    - https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.108-windows-x64-installer
- VS Code or similar editor
    - With https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp
- Other tools I will use today
    - Command prompt/powershell
    - Postman
    - Git (Tortoisegit, Github)

# C#
## According to Wikipedia
C# (pronounced C sharp) is a general-purpose, multi-paradigm programming language encompassing strong typing, lexically scoped, imperative, declarative, functional, generic, object-oriented (class-based), and component-oriented programming disciplines.
- General purpose language
- Strongly Typed
- Object Oriented
- History, Open Source status
- Anatomy of a POCO
- Anatomy of an 'n-teir web app'
- Anatomy of our project
- Anatomy of a controller

# Exercise
1. Prerequisite 
- Make a new folder CSharpService

2. Every front end needs services that connect it to the backend/data storage
    1. Front end will be a simple provided Angular App
    2. Get this from Github
    - git clone https://github.com/harlannorth/todo-app.git
    3. Run from command line
    - cd todo-app
    - npm install
    - ng serve
    - open http://localhost:4200/
3. Get project scaffolding
    1. In CSharpService create a new folder TodoApi
    2. Open Terminal to CSharpeService/TodoApi
    3. run `dotnet new webapi -i TodoApi`
    4. Open this folder in your editor
4. Handle debris
- Delete the ValuesController.cs
- update line 24 of launch settings to 
```
      "launchUrl": "api/todos",
      "applicationUrl": "http://localhost:3000",
```
5. Handle CORS by updating startup.cs
- line 22 add 
```
readonly string MyAllowSpecificOrigins = "_myAllowSpecificOrigins";
```
- Line 29 add
```
              services.AddCors(options =>
                {
                    options.AddPolicy(MyAllowSpecificOrigins,
                    builder =>
                    {
                        builder.WithOrigins("http://localhost:4200");
                    });
                });
```
- Line 53 add
```
app.UseCors(MyAllowSpecificOrigins);
```
4. Create Model
    1. Create new Models folder in TodoApi
    2. Add file in Models folder named TodoItem.cs
    3. Put this code in 
    ```
    namespace TodoApi.Models
    {
        public class TodoItem
        {
            public long Id { get; set; }
            public string Name { get; set; }
            public bool IsComplete { get; set; }
        }
    }
    ```
    4. Note that this matches out Todo.ts!
6. Create a controller
- New file in the Controllers Folder called TodoController.cs
- Insert code outline
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using TodoApi.Models;

namespace TodoApi.Controllers
{

    [Route("api/[controller]")]
    [ApiController]
    public class TodoController : ControllerBase
    {
        private static long? TodoCount;
        private static Dictionary<long, TodoItem> Todos;

        public TodoController()
        {
            if (!TodoCount.HasValue)
            {
                TodoCount = 0;
            }

            if (Todos == null)
            {
                Todos = new Dictionary<long, TodoItem>();
            }

        }

    }
}
```
7. Note theDatastore
This is a simple static dictionary that will only live as long as our service is running.
```
        private static long? TodoCount;
        private static Dictionary<long, TodoItem> Todos;
```
8. Also note the constructor sets everything up
```
        public TodoController()
        {
            if (!TodoCount.HasValue)
            {
                TodoCount = 0;
            }

            if (Todos == null)
            {
                Todos = new Dictionary<long, TodoItem>();
            }

        }
```
7. Implement Post Operation
    1. Do Code
    ```
            // POST api/values
        [HttpPost]
        public TodoItem Post([FromBody] TodoItem value)
        {
            if (Todos == null)
            {
                throw new Exception("Todos is null");
            }

            var insertValue = new TodoItem {
                Id = TodoCount.Value,
                IsComplete = value.IsComplete,
                Name = value.Name
            };

            if (!Todos.TryAdd(TodoCount.Value, insertValue))
            {
                throw new Exception("Todo already exists");
            }
            
            TodoCount++;
            return insertValue;
        }
     ```
    2. Spin up service from command line
    3.  Demonstrate working code with postman
    4. Connect with angular app
8. Implement a Get All Operation
    1. Do code
    2. Spin up service from command line
    3. Demonstrate working with postman
    4. Connect with angular app
9. Implement a Get Single Operation
    1. Do code
    2. Spin up service from command line
    3. Demonstrate working with postman
    4. Connect with angular app
10. Implement Put/Update Operation
    1. Do Code
    2. Spin up service from command line
    3. Demonstrate working code with postman
    4. Connect with angular app
11. Implement Delete Operation
    1. Do Code
    2. Spin up service from command line
    3. Demonstrate working code with postman
    4. Connect with angular app
12. What we learned from this
    1. Simple process that could be dockerized provides back end for front end application
# References
- https://docs.microsoft.com/en-us/aspnet/core/getting-started/?view=aspnetcore-2.2&tabs=windows
- https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-2.2&tabs=visual-studio
- https://www.sitepoint.com/angular-2-tutorial/  (THIS IS OLD AVOID IT)
- https://en.wikipedia.org/wiki/C_Sharp_(programming_language)
# Important Topics not covered
- .Net Core
- In depth HTTP 
- Object Oriented / Inheritance / Interfaces
- Unit Testing
- IL / .Net (what makes C# into machine code)
- Dependency Injection
- Error Handling
- Async/Await, Tasks, concurrency
- IIS & other web servers
- Nuget
- Angular (in any way)
- EntityFramework
