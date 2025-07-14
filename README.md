# Playwright Product Monitor

This project is an automated product monitoring tool built with Playwright and Node.js. It is designed to:

- Monitor product search results on e-commerce sites such as Teknosa and MediaMarkt.
- Detect changes in product price or availability for specific search keywords.
- Send an email notification when a change (such as a discount or stock update) is detected.
- Run automatically every day at 12:00 UTC using GitHub Actions.

## What the Script Does
- Uses Playwright to search for products on each configured site.
- Extracts product information (name, price, availability) and compares it to previous runs.
- If a change is detected, sends an email to the configured recipient with details of the change.
- Stores product history to avoid duplicate notifications.
- Supports both headless and headed browser modes for flexibility in local debugging and CI environments.
- The monitor script randomly selects between Chromium, Firefox, and WebKit browsers for each run.
- **Automatically handles cookie consent popups on monitored sites.**
- **Scrapes all monitored sites in parallel for faster execution.**

## Usage
- To run the monitor script locally, use:
  ```
  npx ts-node tests/monitor.ts
  ```
- The selected browser will be printed in the console output (tagged with [DEBUG]).
- Make sure your environment variables for SMTP and email are set if you want to enable email notifications.
- **Email notifications require both the environment variables and the `ENABLE_EMAIL` flag set to `true` in the code.**

## What Was Implemented
- Product monitoring logic for multiple e-commerce sites.
- Change detection for price and availability.
- Email notification system using environment variables for SMTP credentials and recipient address.
- GitHub Actions workflow for scheduled, automated execution in the cloud.
- Configurable search keywords and monitored sites.
- English-only codebase and documentation.

---
This project is intended for automated, scheduled product monitoring and notification. All configuration and logic are implemented in the code and workflow files.