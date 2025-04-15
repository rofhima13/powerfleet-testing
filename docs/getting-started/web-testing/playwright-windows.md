# Getting Started with Playwright & C# on Windows

**Author:** Rofhiwa 'Ralph' Matumba

Welcome! This guide will help you set up your Windows machine to develop and run automated tests using Playwright with C#. We'll install the necessary tools like .NET, VS Code, Playwright itself, and some helpful utilities.

## Prerequisites: Setting Up Your Windows Environment

Let's get the essential software installed first.

### 1. Microsoft .NET Runtime & SDK

Playwright for C# runs on the .NET platform. This project requires **.NET 9.0** (as of April 2025).

* **Download .NET 9:** Visit the official download page: [.NET 9.0 Download](https://dotnet.microsoft.com/en-us/download/dotnet/9.0)
* **Install Components:** Download and install **both** of the following for x64 systems:
  * **.NET SDK (x64):** The Software Development Kit is needed for building (compiling) the C# code.
  * **ASP.NET Core Runtime (x64):** The runtime is needed to execute applications and test components.
* Run both installers, using the default settings.

### 2. Visual Studio Code (VS Code)

A code editor or IDE is where you'll write your tests. VS Code is a recommended, free option.

* **Option A: Download from Website:** Get the installer from [code.visualstudio.com/download](https://code.visualstudio.com/download) and run it.
* **Option B: Install via `winget`:** If you have Windows Package Manager (`winget`), you can open PowerShell or Command Prompt and run:

```bash
winget install Microsoft.VisualStudioCode
```

### 3. Node.js and npm

Playwright uses Node.js's package manager (npm) to install the Playwright library and manage the browser binaries it needs.

* **Install Node.js:** Download the LTS (Long Term Support) version installer from [nodejs.org](https://nodejs.org/) and run it with default settings (ensure "Add to PATH" is enabled).
* **Or Install via `winget`:**

```bash
winget install OpenJS.NodeJS.LTS
```

* **Verify (Optional):** Open a *new* PowerShell/Command Prompt and check versions using `node -v` and `npm -v`.

## Step 2: Getting the Project Code

1. **Azure Authentication:** Make sure your machine is set up to securely connect to Azure DevOps using HTTPS or SSH. If you haven't done this, follow the steps outlined in the Git/Azure setup guide: [Azure Authentication Setup](../../misc/azure.md) (Ensure this link points to the correct local file or URL).
2. **Choose & Clone Repository:** The team uses several Playwright repositories:
    * `PlaywrightRegression`
    * `PlaywrightV2`
    * `PlaywrightUnity`
    For getting started, clone **`PlaywrightV2`**.
3. **Clone:** Open PowerShell/Command Prompt, navigate (`cd`) to where you want to store projects, and use `git clone` with the repository's URL from Azure DevOps:

```powershell
# Example - Replace with the actual URL from Azure DevOps "Clone" button
git clone <URL_for_PlaywrightV2_Repo>
cd PlaywrightV2
```

## Step 3: Setting Up Playwright and Reporting Tools

Now, let's install Playwright into the project and set up the Allure reporting tool.

### 1. Installing Playwright

* **Initialize Playwright:** In your terminal (inside the `PlaywrightV2` folder), run this command:

```bash
npm init playwright@latest --yes -- --quiet --browser=chromium --browser=firefox --browser=webkit --gha
```

  * `npm init playwright@latest`: Starts the Playwright setup for the project.
  * `--yes`: Accepts default prompts.
  * `--`: Separates npm options from Playwright's options.
  * `--quiet`: Less verbose output.
  * `--browser=...`: Downloads specified browser binaries needed for testing.
  * `--gha`: Optionally adds GitHub Actions workflow files (omit if not needed).

### 2. Installing Scoop and Allure (for Reports)

Allure creates detailed, interactive test reports. We'll use Scoop, a command-line installer for Windows, to easily install Allure.

* **Allow Scoop Installation Scripts:** First, ensure PowerShell can run the necessary scripts. Open PowerShell **as Administrator** and run:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
```

*(You can close the Administrator PowerShell after this)*
* **Install Scoop:** Open a regular PowerShell window and run this command to download and install Scoop:

```powershell
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
# Shorthand: irm get.scoop.sh | iex
```

* **Install Allure using Scoop:** Once Scoop is installed, run:

```powershell
scoop install allure
```

## Step 4: Configuring VS Code

Enhance your VS Code experience for C# and Playwright development.

1. **Open the Project:** Launch VS Code, select `File` > `Open Folder...`, and choose the `PlaywrightV2` folder you cloned.
2. **Install Recommended Extensions:**
    * Click the Extensions icon (looks like square blocks) on the left sidebar.
    * Search for and install these extensions:
        * `C# Dev Kit`: Essential for C# development (code completion, debugging, etc.).
        * `Playwright Test for VSCode`: Adds features to run/debug Playwright tests directly from VS Code's interface.
        * `Excel Viewer`: Helpful if test data or configurations are stored in Excel files within the project.

## Step 5: Building the .NET Project

Compile the C# code to make sure everything is ready.

1. **Clean (Optional):** Open a terminal (PowerShell or Command Prompt) inside the `PlaywrightV2` folder and run:

```bash
dotnet clean
```

*(This removes old build files)*
2. **Build:** Compile the project:

```bash
dotnet build
```

## Step 6: Running Tests

Now you should be ready to run tests.

1. **Navigate:** Within the `PlaywrightV2` folder structure, find the test files (e.g., inside a path like `Unit Tests\Individual Tests`).
2. **Find a Test:** Open a C# file (`.cs`) in this directory. Look for methods (functions) marked with attributes like `[TestMethod]`, `[Fact]`, or `[Test]`. These are the actual test cases.
3. **Run from VS Code:** Use the features provided by the VS Code extensions:
    * **Gutter Icons:** Look for small "Run Test" or "Debug Test" icons directly next to the test method definition in the editor gutter. Click these to run or debug that specific test.
    * **Test Explorer:** Look for a "Testing" icon (often looks like a beaker or flask) in the VS Code activity bar on the left. This panel discovers and lists your tests, allowing you to run them individually or in groups.

* **Note:** If you encounter issues running tests via the VS Code UI, you can typically also run them from the command line using `dotnet test` within the project directory. Consult the Playwright Test extension documentation for troubleshooting if needed.

You're now set up to work with Playwright tests on Windows!

Happy testing!
