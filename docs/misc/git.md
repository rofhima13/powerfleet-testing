# Getting Started with Git for Version Control

**Author:** Rofhiwa 'Ralph' Matumba

Welcome! To work effectively with the code repositories stored in Azure DevOps, you'll need a tool called **Git**. Git is a **Version Control System (VCS)**. Think of it as a powerful "undo" button and collaboration tool for code. It tracks changes made to files over time, allows multiple people to work on the same project without overwriting each other's work, and lets you synchronize your local code with the central repository in Azure DevOps.

This guide covers installing Git and understanding a basic workflow.

## Installing Git

First things first, let's get Git installed on your computer.

1. **Download Git:** Go to the official Git website and download the installer for your operating system (Windows link provided below):
    * [Download Git for Windows](https://git-scm.com/downloads/win)
2. **Run the Installer:** Open the downloaded file and proceed through the installation steps.
3. **Use Default Settings:** The default settings selected during installation are suitable for most users. You can generally click "Next" through all the options.
4. **Verify Installation:** Once installed, open your terminal (PowerShell, Git Bash, Command Prompt) and type the following command, then press Enter:

```bash
git --version
```

If Git is installed correctly, you'll see the installed version number printed (e.g., `git version 2.40.0.windows.1`).

## Understanding a Basic Git Workflow

Git can seem a bit complex at first, but you'll primarily use a few core commands for daily work. If you're completely new to Git, searching online for "beginner git tutorial" will yield many great resources (like those on the official Git site, GitHub Docs, Atlassian, or freeCodeCamp).

Here’s a very common, simplified workflow you'll often follow when working with a repository you've already cloned (copied) to your machine:

1. **`git pull`**: **Get Latest Changes.**
    * *What it does:* Before you start making your own changes, get the latest updates that others might have pushed to the central repository in Azure DevOps. `git pull` fetches these changes and merges them into your local copy.
    * *When to use it:* Run this when you start working on the project for the day, or before starting a new task, to ensure you're working with the most up-to-date code.

```bash
# Make sure you are inside your project's directory first!
cd path\to\your\MiXIntegrate # Or other repo folder
git pull
```

1. **Make Your Code Changes:**
    * Edit files, add new files, or delete files using your code editor (like VS Code, NetBeans, IntelliJ).

2. **`git status`**: **Check Your Changes.**
    * *What it does:* Shows you which files you've modified, added, or deleted since your last save (commit).
    * *When to use it:* Frequently, to see the state of your working directory.

```bash
git status
```

1. **`git add <file>` or `git add .`**: **Stage Your Changes.**
    * *What it does:* Selects ("stages") the specific changes you want to include in your next save point (commit). You can stage individual files or use `.` to stage all modified/new files in the current directory and subdirectories.
    * *When to use it:* After making changes and before committing, to prepare the changes for the commit.

```bash
# Stage a specific file
git add src/test/my_new_test.java

# Or stage all changes in the current directory and below
git add .
```

1. **`git commit -m "Your descriptive message"`**: **Save Your Changes Locally.**
    * *What it does:* Creates a snapshot (a "commit") of your staged changes in Git's history *on your local machine*. The `-m` flag lets you provide a brief message describing what you changed (e.g., "Fix login test for new button ID", "Add validation for user input"). Good commit messages are important!
    * *When to use it:* After staging changes, to permanently record them in your local Git history.

```bash
git commit -m "Update Customers test with correct XPath"
```

1. **`git push`**: **Share Your Changes.**
    * *What it does:* Uploads your locally committed changes to the central repository on Azure DevOps, making them available to the rest of the team.
    * *When to use it:* After committing your changes locally, when you're ready to share them.

```bash
git push
```

This `pull -> change -> add -> commit -> push` cycle is fundamental. There's much more to Git (like branching, merging, handling conflicts), but mastering this basic workflow is the essential first step!
