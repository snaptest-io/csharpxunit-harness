# SnapTest C# XUnit Harness

This is a scaffolding project to get started with C#, XUnit & SnapTest generated code.

### Getting started

Clone this repository.
Install the snaptest-cli via `npm install -g snaptest-cli`.

### Generating the SnapTest tests

You will generate the tests via a snaptest CLI command.  The easiest way get the command is via the chrome extension's "generate code" icon ![code](https://res.cloudinary.com/snaptest/image/upload/v1535423547/READMEs/Screen_Shot_2018-08-27_at_9.32.07_PM.png) next to the folder/test you want. 

Example CLI command: `snaptest -r csharp -s xunit -t <your access token> -a <user/project/org> -d <me/userid/projectid>`

For more in-depth options, check out the [snaptest-cli readme](https://www.npmjs.com/package/snaptest-cli).

### Before running your tests

1. If you're snaptest tests utilize environments, you'll need to set them up in this project.  Test/Environment data is passed in to the tests using .NETs configuration builder via the SnapTest.cs "glue" file.  It currently
uses the "In-memory collections" config provider, but can pull data from many sources: [Microsoft.Extensions.Configuration](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-2.1)  

1. To run the tests, you'll need a Selenium server running & Chromedriver. 

This project is setup to test in Chrome, so you'll need [chromedriver](http://chromedriver.chromium.org/downloads).  We've included a standalone version of the selenium server in the /selenium 
folder which you can run via:

`java -jar ./selenium/selenium-server-standalone-3.0.0-beta3.jar`

It's recommended to get a grid server running, ideally via [selenium docker](https://github.com/SeleniumHQ/docker-selenium).   

### SnapConfig.cs
 
This file is required for Snaptest tests to run.  It provides:
- loading environment/test data configuration into the tests.
- extending the basic suite/test/action reporting.
- configuring of the target selenium server, concurrency, and browser type.  

### Running with .NET test driver

Run ```dotnet test``` to run all your tests

#### Options

##### View test output:
```dotnet test --logger=trx```
This command will generate an XML report of the tests ran.

