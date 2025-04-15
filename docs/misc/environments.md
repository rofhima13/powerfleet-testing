# Understanding Our Application Environments

Welcome! At Powerfleet (formerly MiX Telematics), our fleet management platform isn't just one single website. We operate several different versions, called **environments**, to serve various regions and purposes like development, testing, and production. Knowing which environment you're testing against is essential for running the right tests and interpreting results correctly.

## List of Key Environments

Here are the main environments you'll likely interact with, along with their abbreviations and URLs:

* **ALG (Algeria)**: `alg.mixtelematics.com`
  * Serves the Algeria region.
* **AU (Australia)**: `au.mixtelematics.com`
  * Serves the Australia region.
* **CPT (South Africa / Cape Town)**: `za.mixtelematics.com`
  * Serves the South Africa region.
* **ENT (Enterprise)**: `ent.mixtelematics.com`
  * A specific environment often used for large enterprise clients.
* **INT (Integration)**: `int.mixtelematics.com`
  * This is our main **development and integration testing** environment. It typically has the very latest code changes and newest features, making it "cutting-edge" but potentially less stable than others. Most new feature testing happens here first.
* **OMN (Oman)**: `om.mixtelematics.com`
  * Serves the Oman region.
* **UAE (United Arab Emirates)**: `uae.mixtelematics.com`
  * Serves the UAE region.
* **UAT (User Acceptance Testing)**: `uat.mixtelematics.com`
  * This is a **pre-production** environment. It's used for final testing and validation by internal teams or sometimes clients before features are released to the live production environments. It should be much more stable than INT.
* **UK (United Kingdom)**: `uk.mixtelematics.com`
  * Serves the UK region.
* **US (United States)**: `us.mixtelematics.com`
  * Serves the US region.

## Accessing Environments in Test Code

When writing or running automated tests, you won't usually type these URLs directly. Instead, these environment identifiers (like `INT`, `UAT`, `US`, etc.) are typically defined as constants within the test automation code, often found within an `Enums` package or similar configuration area in each web testing module. This allows tests to easily switch target environments.
