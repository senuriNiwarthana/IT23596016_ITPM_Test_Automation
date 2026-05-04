# Chat Sinhala Transliteration – Playwright Automation

Automated negative test suite for the **Chat Sinhala** transliteration function at [pixelssuite.com/chat-translator](https://www.pixelssuite.com/chat-translator).

This project automates **50 negative test cases** (Neg\_0001 – Neg\_0050) that cover all 24 Singlish input types defined in the assignment appendix and records actual outputs alongside pass/fail status directly in the provided Excel file.

---

## Project Structure

```
test_automation/
├── test_automation.py          # Main Playwright automation script
├── Assignment 1 - Test cases.xlsx  # Excel file with test data & results
├── requirements.txt            # Python dependencies
├── .gitignore                  # Git ignore rules
└── README.md                   # This file
```

---

## Prerequisites

| Requirement | Version | Notes |
|---|---|---|
| Python | 3.11 or 3.12 | [python.org](https://www.python.org/downloads/) |
| Google Chrome | Latest | Recommended browser |
| pip | Latest | Bundled with Python |

---

## Installation (one-time setup)

Open **Command Prompt** and navigate to the project folder:


Upgrade pip and install dependencies:

```cmd
pip install -U pip
pip install playwright openpyxl
playwright install
```

> **Note:** `playwright install` downloads the browser binaries (~300 MB). Requires an internet connection.

---

## Running the Tests

From the project root (`D:\test_automation`), run:

```cmd
python test_automation.py --excel "Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 5000 --type-delay-ms 80 --slow-mo-ms 200 --save-every 1 --keep-open
```

### Command-line Arguments

| Argument | Default | Description |
|---|---|---|
| `--excel` | `Assignment 1 - Test cases.xlsx` | Path to the Excel test-case file |
| `--url` | `https://www.pixelssuite.com/chat-translator` | Target application URL |
| `--wait-ms` | `5000` | Milliseconds to wait for transliteration output |
| `--type-delay-ms` | `80` | Delay between keystrokes (ms) to simulate human typing |
| `--slow-mo-ms` | `200` | Playwright slow-motion delay (ms) |
| `--save-every` | `1` | Save Excel after every N test cases |
| `--keep-open` | *(flag)* | Keep browser open after all tests complete |
| `--headless` | *(flag)* | Run in headless mode (no browser window) |
| `--retries` | `8` | Retry attempts when waiting for output |
| `--retry-wait-ms` | `1000` | Wait between retries (ms) |
| `--timeout-ms` | `60000` | Overall page/element timeout (ms) |

---

## Checking Results

1. After the script finishes (or while `--keep-open` is active), open **`Assignment 1 - Test cases.xlsx`**.
2. The **`Actual output`** and **`Status`** columns are automatically populated.
3. Status values:
   - `PASS` – Actual output matches Expected output exactly.
   - `FAIL` – Actual output differs from Expected output (the test case documents a defect).
   - `UI Error` – The automation could not interact with the page for this row.

---

## Test Case Coverage

The 50 negative test cases (IDs: `Neg_0001` – `Neg_0050`) cover the following Singlish input types:

| # | Singlish Input Type | Test Cases |
|---|---|---|
| 1 | Question forms | Neg_0001, Neg_0002 |
| 2 | Command forms | Neg_0003, Neg_0004 |
| 3 | Greetings | Neg_0005, Neg_0006 |
| 4 | Requests | Neg_0007, Neg_0008 |
| 5 | Responses | Neg_0009, Neg_0010 |
| 6 | Repeated Words | Neg_0011, Neg_0012 |
| 7 | Inputs with Punctuation Marks | Neg_0013, Neg_0014 |
| 8 | Romanization / Spelling Variants | Neg_0015, Neg_0016 |
| 9 | Isolated English Word Insertions | Neg_0017, Neg_0018 |
| 10 | Multi-Word English Phrases | Neg_0019, Neg_0020 |
| 11 | English Digital Terms | Neg_0021, Neg_0022 |
| 12 | Platform/App Names | Neg_0023, Neg_0024 |
| 13 | English Abbreviations/Acronyms | Neg_0025, Neg_0026 |
| 14 | English Clipped Forms | Neg_0027, Neg_0028 |
| 15 | Place Names Embedded in Singlish | Neg_0029, Neg_0030 |
| 16 | Person Names Embedded in Singlish | Neg_0031, Neg_0032 |
| 17 | Inputs with Numbers and Numeric Suffixes | Neg_0033, Neg_0034 |
| 18 | Inputs with Currency | Neg_0035, Neg_0036 |
| 19 | Inputs with Time Formats | Neg_0037, Neg_0038 |
| 20 | Inputs with Dates | Neg_0039, Neg_0040 |
| 21 | Inputs with Unit of Measurements | Neg_0041, Neg_0042 |
| 22 | Inputs with Slang and Casual Phrasing | Neg_0043, Neg_0044 |
| 23 | Online Identifiers in Singlish | Neg_0045, Neg_0046 |
| 24 | Inputs Containing Emojis | Neg_0047, Neg_0048 |
| *(any)* | Mixed / Additional | Neg_0049, Neg_0050 |

---

## Notes

- This automation targets the **Chat Sinhala** transliteration mode only. Standard Sinhala mode, backend APIs, performance, scalability, and security testing are **out of scope**.
- All 50 test cases are **negative** — they are designed to expose scenarios where the application fails to produce the correct Sinhala output.
- Do not edit the `Actual output` or `Status` columns manually; they are managed by the automation script.
