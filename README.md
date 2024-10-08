# Goal

The goal is to create a Minimal WebAPI using .NET 8.0 and a corresponding Docker image with the help of GitHub Copilot.
Follow the instructions below and try to use GitHub Copilot as much as possible.
Try different things and see what GitHub Copilot can do for you, like generating a Dockerfile or a class, add comments, etc.

> Make sure GitHub Copilot is configure and enabled for the current laguage, just check the status bar on the bottom right corner of VS Code.

> If you are running this exercise in local environment, please make sure .NET 8 is installed.

> If you are running this exercise in GitHub Codespaces, the .NET 8 environment is already setup.

## Instructions

The `copilot-demo` folder contains the `MinimalAPI.sln` solution, with 2 projects:

- `MinimalAPI` is a minimal WebAPI project created using `dotnet new webapi -minimal`
- `MinimalAPI.Tests` is a minimal xUnit project created using `dotnet new xunit`
- `Dockerfile` will be used to create a docker image for the project.

To run Copilot inline on Windows you press `Ctrl + i` (Windows) / `⌘ + i` (Mac)

To run the app open a terminal in the `copilot-demo` folder and run:

```sh
dotnet run --project ./MinimalAPI/MinimalAPI.csproj
```

To run the tests, open a terminal in the `copilot-demo` folder and run:

```sh
dotnet test
```

### Exercise 1: Hello World!

For this exercise we will be adding a new endpoint to handle a simple GET request.

- Move to the `MinimalAPI/Program.cs` file
- Add a new Hello World endpoint at `/` that returns a `Hello World!` string.
- Start writing the code to handle `/` and wait a couple of seconds, Copilot will generate the code for you.
- Alternatively, you can test the Copilot inline feature by pressing `ctrl/⌘ + i`. Then write in the text box the desired behaviour.

You can now run the application and then test it with curl.

1. Run the spring app: `dotnet run --project ./MinimalAPI/MinimalAPI.csproj`
2. Test with curl: `curl -v "http://localhost:5163/"`
3. If you are using GitHub `Codespaces`, replace localhost:5163 with actual `Codespaces` url.

### Exercise 2: Write a Hello GET Request

For this exercise we will be adding a new endpoint to handle a simple GET request.

- Move to the `MinimalAPI/Program.cs` file
- Start writing the code to handle a simple GET request based on the following prompt:

```cs
/*
* Create a `/hello` GET endpoint to return the value of a query parameter called key.
* If the key is not passed, return "key not passed".
* If the key is passed, return "hello <key>".
*
*/
```

- Alternatively, you can test the Copilot inline feature by pressing `ctrl/⌘ + i`. Then write in the text box the desired behaviour.

You can now run the application and then test it with curl.

1. Run the spring app: `dotnet run --project ./MinimalAPI/MinimalAPI.csproj`
2. Test with curl: `curl -v "http://localhost:5163/hello?key=world"`
3. If you are using GitHub `Codespaces`, replace localhost:5163 with actual `Codespaces` url.

### Exercise 3: Write a Test Case

There is an existing unit test under `MinimalAPI.Tests/IntegrationTests.cs`, run the below command to test it.

- run `dotnet test`
- If the test passed you should see an output like this:

```sh
Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     1, Skipped:     0, Total:     1, Duration: < 1 ms - MinimalAPI.Tests.dll (net8.0)
```

Let's now create a new unit test for the `/hello` endpoint. There should be a test for if a key is provided, and another test for if a key is not provided.

- Move to the `MinimalAPI.Tests/IntegrationTests.cs` file
- Create a comment with `//` and ask it to generate the test case for you. Wait a couple of seconds and it should autocomplete the test for you.
- You should then see the following output

```sh
Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     3, Skipped:     0, Total:     3, Duration: 4 ms - MinimalAPI.Tests.dll (net8.0)
```

### Exercise 3: Building new functionalities

For this exercise, the code will live inside `MinimalAPI/Program.cs`

Add the following endpoints using the help of Copilot, then also create the unit tests for every new operation.

- **/daysbetweendates**:

  - calculate days between two dates
  - receive by query string two parameters `date1` and `date2`, and calculate the days between those two dates.

> **_NOTE:_** Use above information inside the Copilot inline feature. Press enter and wait for Copilot to suggest you the code.

- **/validatephonenumber**:

  - receive by querystring a parameter called phoneNumber
  - validate phoneNumber with Spanish format, for example `+34666777888`
  - if phoneNumber is valid return true

> **_NOTE:_** Use above information inside a comment. Press enter and wait for Copilot to suggest you the code.

- **/validatespanishdni**:

  - receive by querystring a parameter called dni
  - calculate DNI letter
  - if DNI is valid return "valid"
  - if DNI is not valid return "invalid"

> **_NOTE:_** Use above information inside a comment. In this case, you may want to see multiple solutions from Copilot to pick the one that best fits the way to calculate the letter. In order to see the firs 10 suggestions from Copilot press `ctrl/⌘ + enter`.

- **/returncolorcode**:

  - receive by querystring a parameter called color
  - read colors.json file and return the rgba field
  - get color var from querystring
  - iterate for each color in colors.json to find the color
  - return the hex field
  - return 404 if not found

> **_NOTE:_** Hint: Use TDD. Start by creating the unit test and then implement the code.
> Lets try Copilot chat now.
> Paste the above information and make it as detailed as possible in the Copilot chat text box.
> Copilot will use by default the open file as context in order to generate the suggestion.

### Exercise 4: Building more integrations

We have tried out write coding for a few simple tasks earlier. Now let's explore more complex integrations.

- **/tellmeajoke**:

  - Make a call to the joke api and return a random joke - <https://api.chucknorris.io/jokes/random>

> **_NOTE:_** Here's example where you might need to use you own knowledge and judgement
> to validate that Copilot follows best practices. Just because Copilot mimics
> what many developers do, doesn't always mean it's the correct way. You might need
> to be extra specific in your prompt to let Copilot know what's best practices.

- **/moviesbydirector**:

  - Receive by querystring a parameter called director
  - Make a call to the movie api and return a list of movies of that director
  - Return the full list of movies

> **_NOTE:_** This will require to browse to <https://www.omdbapi.com/apikey.aspx> and request a FREE API Key

- **/parseurl**:

  - Retrieves a parameter from querystring called someurl
  - Parse the url and return the protocol, host, port, path, querystring and hash
  - Return the parsed host

> **_NOTE:_** Copilot can help you learn new frameworks.

- **/listfiles**:

  - Get the current directory
  - Get the list of files in the current directory
  - Return the list of files

> **_NOTE:_** Copilot can also help with these kind of commands locally. The feature is called Copilot in the CLI. You can learn more information about this feature [here](https://docs.github.com/en/copilot/github-copilot-in-the-cli/about-github-copilot-in-the-cli).

- **/calculatememoryconsumption**:

  - Return the memory consumption of the process in GB, rounded to 2 decimals

- **/randomeuropeancountry**:

  - Make an array of european countries and its iso codes
  - Return a random country from the array
  - Return the country and its iso code

### Exercise 5: Document the code

Documenting code is always a boring and painful task. However, we can use Copilot to document it for us. In the chat, ask Copilot to add xml comments to all of your files.

You can use `@workspaces` to write documentation for the whole repo.

### Exercise 6: Verify Tests

Have you been building your Unit Tests along the way? If not this is the perfect time to take a breather and get Copilot to write some unit tests for you!

We will create automated tests to check that the functionality of the previous endpoints is correctly implemented. The tests should be together in the `IntegrationTests.cs` file.

You can leverage Copilot to run the tests. There is a `/tests` command that you can directly run from Copilot Chat or by selecting the piece of code you want to create tests for and using the Copilot inline feature.

### Exercise 7: Create a Dockerfile

Use the Dockerfile provided to create a docker image of the application. There are some comments in the Dockerfile that will help you to complete the exercise.

In order to build, run and test the docker image, you can use Copilot as well to generate the commands.

For instance, create a `DOCKER.md` file where you can store the commands to build, run and test the docker image.

Examples of steps to document: Build the container image, Run the container, Test the container.

## Summary

With the previous exercises you have gone through some common activities that developers usually run:

- Create new features in the code
- Work with external APIs
- Create documentation
- Create tests

However, there are many other things that Copilot can helkp you with. Feel free to explore other slash command in the Copilot chat like:

- `/fix`: to fix the problems in your code
- `/explain`: for Copilot to explain you what the code does
