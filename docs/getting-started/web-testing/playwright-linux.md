# Getting Started with Playwright & C# on Linux (Ubuntu)

**Author:** Rofhiwa 'Ralph' Matumba

Welcome! This guide will walk you through setting up your Ubuntu Linux environment to run automated tests using Playwright with C#. This involves installing several tools and dependencies, but following these steps will get you ready.

## Prerequisites: Setting Up Your Ubuntu Environment

Let's install the core software needed. You'll need administrator privileges (`sudo`) for some commands.

### 1. Microsoft .NET Runtime & SDK

Playwright for C# runs on .NET. This project targets **.NET 6.0**.

* **Install .NET 6:** Open your Terminal and run the following commands. The first updates your package list, the second installs the .NET 6 SDK.

```bash
sudo apt-get update && sudo apt-get install -y dotnet-sdk-6.0
```

* **Verify (Optional):** You can check the installation by running `dotnet --list-sdks`.

### 2. Visual Studio Code (VS Code)

You need a code editor or Integrated Development Environment (IDE) to work with the C# test code. VS Code is a popular choice.

* **Install VS Code:** Download the `.deb` package for Debian/Ubuntu from the official website: [Download VS Code](https://code.visualstudio.com/download)
* Install it using the command line (replace `<path-to-deb-file>` with the actual path to the downloaded file):

```bash
sudo apt install <path-to-deb-file>.deb
```

(Alternatively, you might be able to double-click the `.deb` file to install it via the Software Center).

### 3. Node.js and npm

Playwright uses Node.js's package manager (npm) for installation and managing browser binaries.

* **Install Node.js and npm:** A common way on Ubuntu is using NodeSource repositories for up-to-date versions. Replace `18.x` with the desired LTS version (e.g., 20.x):

```bash
# Download and run the NodeSource setup script
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
# Install Node.js (which includes npm)
sudo apt-get install -y nodejs
```

* **Verify (Optional):** Check versions using `node -v` and `npm -v`.

### 4. PowerShell

Some scripts within this specific test project require PowerShell to run.

* **Install PowerShell:** Use the `snap` package manager (pre-installed on recent Ubuntu versions):

```bash
sudo snap install powershell --classic
```

### 5. Homebrew and Allure (for Reporting)

Allure is a tool used to generate detailed test reports. This project uses Homebrew, a package manager popular on macOS but also available for Linux, to install it.

* **Install Homebrew:** Run this command in your terminal. It downloads and executes the official installation script:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions provided by the script, which include adding Homebrew to your PATH. * **Install Allure:** Once Homebrew is set up, install Allure:

```bash
brew install allure
```

## Step 2: Getting the Project Code

1. **Azure Authentication:** Ensure you have set up authentication (HTTPS or SSH) to connect securely to Azure DevOps, as covered in the previous Git setup guide.
2. **Clone the Repository:** Open your terminal, navigate (`cd`) to where you want to store the project, and clone the specific Playwright repository used by the team (e.g., `PlaywrightV2`).

```bash
# Replace with the actual URL for your team's Playwright repo
git clone <Your-Playwright-Repo-URL-From-Azure-DevOps>
cd <Name-Of-Cloned-Repo-Folder>
```

## Step 3: Setting Up Playwright and Dependencies

Now, let's configure Playwright within the project folder.

1. **Initialize Playwright:** In the terminal, inside the cloned repository folder, run:

```bash
npm init playwright@latest --yes -- --quiet --browser=chromium --browser=firefox --browser=webkit --gha
```

* `npm init playwright@latest`: Initializes Playwright in the project using the latest version.
    * `--yes`: Accepts default prompts during initialization.
    * `--`: Separates `npm init` options from the Playwright script's options.
    * `--quiet`: Reduces the amount of output during installation.
    * `--browser=...`: Tells Playwright to download these specific browser binaries (Chromium, Firefox, WebKit).
    * `--gha`: Adds basic GitHub Actions workflow files for CI/CD (omit this if not needed).

## Step 4: Configuring VS Code

For a better development experience in VS Code:

1. **Open the Project:** Launch VS Code and open the cloned repository folder (`File` > `Open Folder...`).
2. **Install Recommended Extensions:**
    * Go to the Extensions view (click the icon on the left sidebar that looks like four squares, with one detached).
    * Search for and install the following extensions:
        * `C# Dev Kit`: Provides enhanced C# language support (intellisense, debugging).
        * `Playwright Test for VSCode`: Adds specific features for running and debugging Playwright tests directly within VS Code.
        * `Excel Viewer`: Useful if your project uses Excel files for test data or configuration.

## Step 5: Building the .NET Project

Before running tests or project-specific scripts, compile the C# code.

1. **Clean (Optional but Recommended):** In the terminal (still inside the project folder), remove any old build artifacts:

```bash
dotnet clean
```

1. **Build:** Compile the project:

```bash
dotnet build
```

## Step 6: Installing Project-Specific Dependencies

This project includes PowerShell scripts to handle further dependency installations. These scripts install necessary system libraries for Playwright browsers and ensure browser binaries are correctly placed.

1. **Install Linux Dependencies for Playwright:** The path is specific to this project's structure after building:

```bash
# Run using PowerShell (pwsh command)
pwsh Test/KeywordDrivenTestFramework.Tests/bin/Debug/net6.0/playwright.ps1 install-deps
```

1. **Install Playwright Browsers (Project Script):** This script handles browser installation within the project context:

```bash
# Run using PowerShell
pwsh Test/KeywordDrivenTestFramework.Tests/bin/Debug/net6.0/playwright.ps1 install
```

You should now have all the necessary components installed and configured to run Playwright tests from this project on your Ubuntu device.

Happy testing!
