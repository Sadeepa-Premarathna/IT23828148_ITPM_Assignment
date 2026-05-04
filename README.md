# IT23828148 – ITPM Assignment: Singlish-to-Sinhala Translator Test Automation

> **Student ID:** IT23828148  
> **Module:** IT Project Management (ITPM)  
> **Assignment:** Automated Testing of the Singlish-to-Sinhala Translator Web Interface

---

## 📌 Project Overview

This project automates the **black-box functional testing** of the [Pixels Suite Chat Translator](https://www.pixelssuite.com/chat-translator) — a web application that translates Singlish (Romanized Sinhala) into Sinhala script.

The automation framework:
- Reads **50 Singlish test cases** (with expected Sinhala outputs) from an Excel workbook
- Drives a real Chromium browser using **Playwright** to interact with the translator UI
- Records the **actual output** from the translator for each test case
- Evaluates each result as **PASS / FAIL / COLLECTED**
- Writes results back into the same Excel file for reporting

---

## 📁 Repository Structure

```
IT23828148_ITPM_Assignment/
│
├── test_automation.py          # Main Playwright test automation script
├── Assignment 1 - Test cases.xlsx  # Excel workbook with 50 test cases & results
└── README.md                   # This file
```

---

## ⚙️ Prerequisites

Make sure the following are installed on your system before running the tests:

| Tool | Version | Notes |
|------|---------|-------|
| Python | 3.9 or higher | [Download](https://www.python.org/downloads/) |
| pip | Latest | Included with Python |
| Git | Any | To clone this repo |

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Sadeepa-Premarathna/IT23828148_ITPM_Assignment.git
cd IT23828148_ITPM_Assignment
```

### 2. (Recommended) Create a Virtual Environment

```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Python Dependencies

```bash
pip install playwright openpyxl
```

### 4. Install Playwright Browsers

```bash
playwright install chromium
```

---

## ▶️ Running the Tests

### Basic Run (browser visible)

```bash
python test_automation.py
```

This will:
- Open a Chromium browser window (visible)
- Navigate to the translator at `https://www.pixelssuite.com/chat-translator`
- Test all rows in the **` Test cases`** sheet of `Assignment 1 - Test cases.xlsx`
- Write **Actual output** and **Status** (PASS/FAIL) back into the Excel file

---

### Headless Run (no browser window)

```bash
python test_automation.py --headless
```

---

### Common Options

| Flag | Default | Description |
|------|---------|-------------|
| `--excel` | `Assignment 1 - Test cases.xlsx` | Path to the Excel test case file |
| `--sheet` | ` Test cases` | Sheet name inside the workbook |
| `--url` | `https://www.pixelssuite.com/chat-translator` | URL of the translator |
| `--output` | _(same as `--excel`)_ | Path to save results (defaults to input file) |
| `--headless` | `False` | Run browser without UI |
| `--wait-ms` | `5000` | Wait time (ms) after each translation |
| `--retries` | `8` | Retry attempts to read output |
| `--retry-wait-ms` | `1000` | Wait (ms) between retries |
| `--type-delay-ms` | `30` | Delay (ms) between keystrokes |
| `--timeout-ms` | `60000` | Browser operation timeout (ms) |
| `--slow-mo-ms` | `0` | Slow motion delay for Playwright (ms) |
| `--save-every` | `0` | Save Excel every N rows (`0` = only at end) |
| `--keep-open` | `False` | Keep browser open after tests finish |

#### Example with custom options

```bash
python test_automation.py --headless --wait-ms 7000 --save-every 10 --output results_output.xlsx
```

---

## 📊 Understanding the Results

After running, open `Assignment 1 - Test cases.xlsx` and navigate to the **` Test cases`** sheet.

| Column | Description |
|--------|-------------|
| `Singlish` | Input Singlish text fed to the translator |
| `Expected Output` | The expected Sinhala translation |
| `Actual output` | The actual output captured from the UI |
| `Status` | `PASS` – matches expected · `FAIL` – does not match · `COLLECTED` – no expected value provided |

---

## 🛠️ Troubleshooting

**`Error: Could not find Chat UI locators`**  
→ The translator page may have changed its layout. Try increasing `--timeout-ms` or running without `--headless` to inspect the page.

**`Error: File '...' not found`**  
→ Ensure you are running the script from the repository root directory, or pass the `--excel` flag with the correct path.

**`playwright: command not found`**  
→ Make sure your virtual environment is activated and Playwright is installed (`pip install playwright`).

**Tests show `UI Error` in Status column**  
→ The translator may be slow or unavailable. Try increasing `--wait-ms` and `--retries`.

---

## 📝 Test Case Coverage

The 50 test cases cover the following linguistic categories:

- ✅ Basic common phrases & greetings
- ✅ Everyday conversational Singlish
- ✅ Grammar edge cases (tense, plural, negation)
- ✅ Colloquial / slang expressions
- ✅ Mixed Sinhala-English (code-switching) inputs
- ✅ Long sentences and compound phrases
- ✅ Special characters and punctuation handling
- ✅ Numerals and digits within text

---

## 📄 License

This project is submitted as part of the **ITPM module** assessment at **SLIIT**. All rights reserved © 2024 IT23828148.