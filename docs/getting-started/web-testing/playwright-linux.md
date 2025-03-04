# Getting Started with Playwright on Linux (Ubuntu)

## Prerequisites

Before running the Playwright test suite on Ubuntu, make sure to install the necessary dependencies.

### Microsoft .NET
Start by installing Microsoft .NET. While the latest version works, it's recommended to install the targeted version, which is .NET 6.0. You can do this via APT with the following command:
```bash
sudo apt-get update && sudo apt-get install dotnet6
```

### VS Code
Next, you'll need a C# compatible IDE. Visual Studio Code (VS Code) is recommended. You can download the latest version from their [website](https://code.visualstudio.com/download).

## Cloning the Playwright Repository
Ensure your device has the proper authentication to clone repositories from Azure. Then clone the Playwright repository and navigate to its folder through the command line.

## Installing Playwright
To install the latest version of Playwright, similar to how you install [browsers](./selenium.md#chrome-chromedriver-and-nodejs) via Node.js, run:
```bash
$ npm init playwright@latest --yes -- --quiet --browser=chromium --browser=firefox --browser=webkit --gha
```
This command will install Playwright along with the recommended browsers.

## PowerShell
You'll need PowerShell to run the installation script for the test suite. Install PowerShell by running:
```bash
$ sudo snap install powershell --classic
```

## Brew and Allure
Finally, install the latest version of Allure, an open-source automation testing report tool, using a third-party package manager. We'll use Homebrew for this. Run the following commands to download and install Homebrew:
```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install Allure through Homebrew:
```bash
$ brew install allure
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
After installing the extensions, return to your command prompt (Terminal), navigate to the Playwright repository, and run the following commands:
```bash
dotnet clean
dotnet build
```

## Installing Ubuntu and PowerShell Dependencies
Once the project is built, install the Linux dependencies using the command below:
```bash
$ pwsh Test/KeywordDrivenTestFramework.Tests/bin/Debug/net6.0/playwright.ps1 install-deps
```

Finally, to install the browser dependencies, run:
```bash
$ pwsh Test/KeywordDrivenTestFramework.Tests/bin/Debug/net6.0/playwright.ps1 install
```

You're now set to run Playwright tests on your Ubuntu device. Happy testing!