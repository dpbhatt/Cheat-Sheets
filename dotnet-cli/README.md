
# dotnet cli cheat sheet
---

## Create a new project

* Get the list of installed templates <br>

    ` dotnet new list `

* Create a new project in the current folder

    `dotnet new [template-name]`
    <br>
    `dotnet new web`
    <br>
    `dotnet new gitignore`
    <br>
    `dotnet new editorconfig`

* Create a new project in a subfolder
  
    `dotnet new [template-name] -n [project-name] -o [output-folder]`
    <br>
    `dotnet new console -o MyApp`
    <br>
    `Dotnet new console -n MyDemoApp -o MyApp`

## Manage Solution files (.sln)

* Create a new solution file named the current directory

    `dotnet new sln`

* Create a new solution file in a subfolder

    `Dotnet new sln -n [solution-name] -out [output-folder]`
    <br>
    `dotnet new sln -o MySolution`
    <br>
    `dotnet new sln -n MySolution -o MySolution`

* List all projects in a solution file

    `dotnet sln list`
    <br>
    `dotnet sln [solution-name] list`

* Add one or more projects to a solution file

    `dotnet sln add [path to the csproj to add]`
    <br>
    `dotnet sln add MyLib\MyLib.csproj`

* Add projects to the solutions (the first is for Unix/Linux-based terminals and the second is in Windows PowerShell)

    `dotnet sln add **/*.csproj`
    <br>
    `dotnet sln add (ls -r **/*.csproj)`

* Remove one or more projects from a solution file

    `dotnet sln remove [Project path]`
    <br>
    `dotnet sln remove MyLib\MyLib.csproj`
    <br>
    `dotnet sln remove **/*.csproj`
    <br>
    `dotnet sln remove (ls -r **/*.csproj)`

## Manage project dependencies

* Add a reference to another project

    `dotnet add reference [Project path]`
    <br>
    `dotnet add reference ../MyLib/MyLib.csproj`

* Add multiple project references to the project in the current directory
  
    `dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

* Remove a project reference

    `dotnet remove reference [Project path]`
    <br>
    `dotnet remove reference ../MyLib/MyLib.csproj`

* List all project references

    `dotnet list reference`

* Add a Nuget package

    `dotnet add package [Package]`
    <br>
    `dotnet add package NewtonSoft.Json`

* Remove a Nuget package

    `dotnet remove package [Package]`
    <br>
    `dotnet remove package NewtonSoft.Json`

* List all project references

    `dotnet list package`

* Restore packages

    `dotnet restore`


## Build

* Build the project or solution in the current folder

    `dotnet build`

* Build the Release configuration

    `dotnet build -c Release`

* Build the project or solution

    `dotnet build [Project/Solution]`
    <br>
    `dotnet build MySolution.sln`

## Run

* Run the project in the current directory

    `dotnet run`

* Run the specified project

    `dotnet run --project [path-to-the-project]`
    <br>
    `dotnet run --project ./projects/project1/project1.csproj`

## Clean

* Clean the project or solution in the current directory

    `dotnet clean`

* Clean the specific project or solution

    `dotnet clean [Project or Solution]`
    <br>
    `dotnet clean ./projects/project1/project1.cspron`

* Clean a project built using the Release configuration

    `dotnet clean -c Release`

* Clean a project built using the Debug configuration

    `dotnet clean -c Debug`


## Test

* Run the tests

    `dotnet test`

* Run the tests and create a test report

    `dotnet test --logger “trx;LogFileName=results.trx”`

* List all tests without running them

    `dotnet test -t`

* Run tests that match the given expression

    `dotnet test --filter [Filter]`
    <br>
    `dotnet test --filter Unit`
    <br>
    `dotnet test --filter “TestCategory=Database”`
    <br>
    `dotnet test --filter “TestCategory!=slow”`
    <br>
    `dotnet test --filter “Unit&(TestCategory=Cat1)”`

## Publish

* Publish the project or solution from the current folder

    `dotnet publish`

* Publish a specific project or solution 

    `dotnet publish [Project or solution path]`
    <br>
    `dotnet publish ./projects/projects.sln`
    <br>
    `dotnet publish ./projects/projects/project1.csproj`

* Build a self-contained executable for Windows
    
    `dotnet publish -c Release -r win-x64 -p:PublishSingleFile=true --self-contained true`

* Build a self-contained executable for Linux
    
    `dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained true`

## Entity Framework core

* Add a new migration

    `dotnet ef migrations add [migration-name]`

* List available migrations

    `dotnet ef migrations list`

* Remove the latest migration

    `dotnet ef migrations remove`

* Generate a SQL script from migrations

    `dotnet ef migrations script`

* Update the database to the latest migration

    `dotnet ef database update`

* Update the database to a specific migration name point

    `dotnet ef database update [migration-name]`

* Drop the database

    `dotnet ef database drop`
    <br>
    `dotnet ef database drop -f`

* List available DbContext types

    `dotnet ef dbcontext list`

* Get information about the DbContext type

    `dotnet ef dbcontext info`

* Scaffolds a DbContext and entity types for a database

    `dotnet ef dbcontext scaffold`

* Check if there are any model changes since the last migration

    `dotnet ef migrations has-pending-model-changes	`

## Global Tools

* Install a global tool

    `dotnet tool install -g [tool-name]`
    <br>
    `dotnet tool install --global dotnet-ef`

* Update a global tool

    `dotnet tool update -g [tool-name]`
    <br>
    `dotnet tool update --global dotnet-ef`

* Uninstall a global tool

    `dotnet tool uninstall -g [tool-name]`

* List all globally installed tools

    `dotnet tool list -g`

## Project Templates

* Install a new project template

    `dotnet new --install [dotnet-template-name]`

* Remove a project template

    `dotnet new --uninstall [dotnet-template-name]`


## Nuget

* Build the project and create Nuget packages

    `dotnet pack`

* Publish a Nuget package

    `dotnet nuget push [package]`
    <br>
    `dotnet nuget push foo.nupkg`

## Miscellaneous

* Display .NET SDK version in use

    `dotnet --version`

* Get help related to all available dotnet commands

    `dotnet --help`

* Get help related to a specific dotnet command

    `dotnet [command-name] --help`
    <br>
    `dotnet new --help`

* List SDKs

    `dotnet --list-sdks`

* List runtimes

    `dotnet --list-runtimes`

* Target a specific SDK

    `dotnet new globaljson --sdk-version [version]`
