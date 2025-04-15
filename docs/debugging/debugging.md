# Finding and Fixing Hiccups: A Beginner's Guide to Debugging Tests

**Author**: Rofhiwa 'Ralph' Matumba

> **"It's a human sign, when things go wrong"**
>> \- Elton John, "Sacrifice" *(Encountering issues is a normal part of development)*

Welcome! When working with automated tests, you'll inevitably encounter situations where they don't run as expected. This is a standard part of the process, and finding and fixing these issues is called **debugging**.

Simply put, debugging means finding and fixing any issues that stop our automated tests from running correctly or giving the right results.

Here are common reasons why a test might fail:

* **Syntax Errors:**
  * These are like typos or grammatical mistakes in the test script code (e.g., a missing bracket `]`, a misplaced comma `,`). They usually prevent the test from starting at all.
  * *Example:* Forgetting a closing parenthesis like `print("Hello"` instead of `print("Hello")`, or misplacing a comma in a function call.

* **Runtime Errors:**
  * These errors occur *during* the test execution when the script tries to do something impossible or invalid at that moment.
  * *Example:* Trying to use a variable that hasn't been assigned a value yet (resulting in a `NameError` or `NullPointerException`), or using an element locator (like an XPath `//button[@id='submit_button']`) that doesn't match any element currently on the page because the ID changed. These typically stop the test mid-execution.

* **Logical Errors:**
  * These can be tricky. The test runs without crashing, but it doesn't validate the right thing, or it produces an incorrect pass/fail result because the underlying logic or assumptions in the test steps are flawed.
  * *Example:* A test verifies that a shopping cart total is greater than $0 (`total > 0`) after adding an item, but it *should* have checked if the total equals the exact price of the item (`total == itemPrice`). The test might pass even if the total is wrong, just as long as it's not zero.

* **Element Not Found Errors:**
  * The test script attempts to find a specific element on the screen (like a button or input field) but cannot locate it within the allowed time.
  * *Example:* The script tries `findElementById('loginButton')` but the element's ID was recently changed to `submitLogin` by developers, or the element is inside an iframe and the script hasn't switched focus to it.

* **Timeout Errors:**
  * The script waits for a certain condition (e.g., an element to become visible, a page to fully load, a background process to finish) but exceeds the maximum allowed waiting time before that condition is met.
  * *Example:* Setting an explicit wait of 15 seconds (`waitForElementVisible(element, 15)`) for an element that, under certain conditions (like slow network), takes 20 seconds to appear.

* **Integration Errors:**
  * These relate to problems with communication between the automated test and external systems it depends on, such as APIs, databases, or other microservices.
  * *Example:* A test needs to fetch setup data from an API before running UI steps, but the API endpoint is down and returns a `503 Service Unavailable` error, preventing the test from proceeding correctly. Or, trying to verify data written to a database, but the database connection fails due to network issues.

* **Flaky Tests:**
  * These tests produce inconsistent results – sometimes passing, sometimes failing – without any apparent changes to the code or application. They often stem from timing issues (race conditions), environmental inconsistencies, or reliance on unstable test data.
  * *Example:* A test clicks an "Add Item" button and immediately checks the cart count. Sometimes it passes, but sometimes the check happens *before* the cart count visually updates on the screen, causing an intermittent failure. Adding a short wait for the count to update might fix it.

* **Maintenance Errors:**
  * When the application under test is updated (UI changes, functionality modifications, text label changes), existing test scripts might become outdated and fail if they haven't been updated accordingly to reflect these changes.
  * *Example:* A test was written to verify the exact text 'Proceed to Checkout' on a button. After a release, the button text is changed to 'Continue to Payment', causing the existing assertion `verifyText(button, 'Proceed to Checkout')` to fail.

Don't worry, you're not alone in figuring these out! This guide covers common approaches to tackle these issues.

## Let Your Code Editor Help You

Pay attention to any hints your code editor (like VS Code, IntelliJ, etc.) gives you! Often, it will underline potential problems (usually in red or yellow). Hovering over these "linting" highlights provides clues about what might be wrong – it's often the first place to look for typos!

## Using Breakpoints: Pausing the Action

Breakpoints are incredibly helpful! They let you pause your test script at specific lines you choose. This allows you to step through the execution slowly, see what the values of variables are at that exact moment, and pinpoint where things start going differently than you expected. Think of it like pausing a video to look closely at a single frame. Mastering breakpoints is a key skill for effective debugging.

## Debugging Tools for Your Specific Setup

Different tools and code editors have built-in features to make debugging easier. We'll explore how to use these in specific environments:

* [How to Debug with Selenium](./selenium.md)

Remember, debugging is a skill that grows with practice. It's okay to not know the answer right away, and asking questions is encouraged – we're all here to help each other succeed!
