# Test Automation for Chat Translator

This project contains an automated testing suite using Python and Playwright to validate a Singlish-to-Sinhala Chat Translator application. It reads test inputs from an Excel file, automates the UI interaction to perform the transliteration, compares the actual output with the expected output, and records the test status back to the Excel file.

## Features

- **Automated UI Testing:** Uses Playwright to interact with a chat translator frontend.
- **Excel Data-Driven Testing:** Reads inputs and expected outputs directly from an Excel spreadsheet.
- **Dynamic Element Interaction:** Smartly finds chat inputs/outputs and action buttons to verify chat responses.
- **Result Logging:** Writes actual outputs and PASS/FAIL results directly back into the test cases Excel file.
- **Headless & Headful Modes:** Supports running tests in the background (headless) or watching the browser interactions.

## Prerequisites

- Python 3.10+
- [Playwright for Python](https://playwright.dev/python/)
- [Openpyxl](https://openpyxl.readthedocs.io/en/stable/) (for Excel file parsing)

To install the necessary dependencies, run:

```bash
pip install playwright openpyxl
playwright install
```

## Usage

Run the script from your command line:

```bash
python test_automation.py [OPTIONS]
```

By default, the script looks for `Assignment 1 - Test cases.xlsx` in the `test_automation` directory and runs against the default frontend URL.

### Command Line Arguments

You can customize the test execution using various arguments:

- `--excel`: Path to the Excel file containing test cases.
- `--sheet`: Name of the sheet to use (default is ` Test cases`).
- `--url`: The target URL for testing (default is `https://www.pixelssuite.com/chat-translator`).
- `--output`: Path to save the updated Excel file with results (defaults to overwriting the input file).
- `--headless`: Run the browser in headless mode (no visible UI).
- `--wait-ms`: How long to wait after transliteration before checking the output (default `5000` ms).
- `--timeout-ms`: Maximum allowed timeout for page load and elements (default `60000` ms).
- `--keep-open`: Keep the browser open after the test is completed (useful for debugging).

### Examples

**Basic execution:**
```bash
python test_automation.py
```

**Running in headless mode:**
```bash
python test_automation.py --headless
```

**Specifying an external Excel file and output location:**
```bash
python test_automation.py --excel "my_test_cases.xlsx" --output "results.xlsx"
```

## Project Structure

- `test_automation.py`: The main automation script that runs the test.
- `Assignment 1 - Test cases.xlsx`: The default data-driven testing sheet containing Singlish inputs and expected Sinhala outputs.
- `.gitignore`: Ignoring `.venv/`, `__pycache__/`, and other auto-generated files.

## Notes

- The script expects certain column headers (e.g., `Input`, `Expected Output`) to figure out where to read and write. If your column names differ slightly, the script uses a normalization heuristic to try to match them.
- If testing fails due to timeouts, you might consider adjusting `--wait-ms` and `--timeout-ms`.
