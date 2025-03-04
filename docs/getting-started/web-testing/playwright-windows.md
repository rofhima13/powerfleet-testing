# Getting Started with Playwright on Windows

## Prerequisites

Before running the Playwright test suite on Windows, ensure you have the required dependencies installed.

### Microsoft .NET
Begin by downloading Microsoft .NET. While the latest version works, it's recommended to install the targeted version, .NET 6.0. You can download it [here](https://dotnet.microsoft.com/en-us/download/dotnet/6.0).

### VS Code
Next, you'll need a C# compatible IDE. Visual Studio Code (VS Code) is recommended. You can get the latest version from their [website](https://code.visualstudio.com/download), or through the Windows Package Manager (winget). To download VS Code via winget, use the command below:
```bash
winget install code
```

## Cloning the Playwright Repository
Ensure your device has the correct authentication info to clone repositories from Azure. Clone the Playwright repository to your device and navigate to its folder through the command line.

### Installing Playwright
To install the latest version of Playwright, similar to installing [browsers](./selenium.md#chrome-chromedriver-and-nodejs) via Node.js, run:
```bash
$ npm init playwright@latest --yes -- --quiet --browser=chromium --browser=firefox --browser=webkit --gha
```
This command installs Playwright along with the recommended browsers.

### Scoop and Allure
Finally, install the latest version of Allure, an open-source automation testing report tool, using a third-party package manager. We'll use the Scoop Package Manager for this. Run the following commands to download and install the latest version of Scoop from their website:
```bash
$ Set-Execution-Policy -ExecutionPolicy RemoteSigned -Scope CurrentUser
$ Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
$ irm get.scoop.sh | iex
```

Then, install Allure via Scoop:
```bash
$ scoop install allure
```

This will install Allure on your system.

## VS Code and Extensions
For efficient use of Playwright with VS Code, download the following extensions:

- C# Dev Kit
- Playwright Test for VS Code
- Excel Viewer

### Installing an Extension
To install an extension, click on the Extensions icon ${extensions} on the left navigation bar in VS Code. Use the search bar above the navigation bar to find and install the mentioned extensions.

## Cleaning and Building
After installing the extensions, return to your command prompt (Powershell) and enter the following commands:
```bash
dotnet clean
dotnet build
```

You're now set to run Playwright tests on your device. Happy testing!