Enterprise Data Cleaning & Governance Pipeline (Python)

A dataset-agnostic, governance-safe data cleaning framework built in Python for real-world business environments.

This system intelligently cleans, validates, and exports datasets while preserving structural integrity and business keys.

🚀 Project Overview

In real-world analytics:

80% of the work is data cleaning

Silent datatype changes break dashboards

ID corruption breaks joins

Excel auto-formatting destroys business keys

This project solves those problems.

It provides:

✔ Intelligent ID detection
✔ Data-driven datatype validation
✔ Strict integrity checks
✔ Duplicate handling
✔ Missing value management
✔ Text normalization
✔ Excel formatting correction
✔ Full audit report generation

🧠 Key Features
1️⃣ Intelligent ID Detection (Score-Based)

Unlike simple keyword matching, this system uses:

Regex boundary-aware keyword detection

Uniqueness ratio scoring

Null ratio scoring

Datetime detection penalty

Weighted ID scoring model

Prevents:

invoicedate being detected as ID

False positives from words containing “id”

Accidental corruption of business keys

Only columns with sufficient ID score are suggested.

2️⃣ Governance-Safe Architecture

The pipeline enforces strict validation:

Row integrity validation after each stage

Column addition/removal detection

Datatype comparison before & after cleaning

No silent datatype conversions

Full action logging

If unexpected structural changes occur → execution stops.

3️⃣ Data-Driven Datatype Review

Each column is evaluated based on actual values:

Numeric compatibility

Datetime compatibility

Time format detection

String fallback

Conversions only occur after user approval.

4️⃣ Duplicate Handling

Options include:

Remove exact duplicates

Flag duplicates without deletion

Skip duplicate handling

All actions are recorded in audit logs.

5️⃣ Missing Value Handling

Strategy depends on datatype:

Numeric → Mean or Median

Text → Fill with "NULL"

ID columns → Controlled fill only

Datetime → Forward fill / NaT / Skip

6️⃣ Text Normalization

Controlled normalization options:

Remove underscores

Remove dashes

Lowercase

Title Case

Uppercase

ID columns are excluded from transformation.

7️⃣ Excel Export with Correct Formatting

Automatically maps pandas dtype → Excel format:

Pandas Type	Excel Format
datetime	dd-mm-yyyy
int	0
float	#,##0.00
percentage-like	0.00%
string/object	@

Prevents Excel from:

Converting IDs to numbers

Stripping leading zeros

Corrupting dates

Breaking postal codes

8️⃣ Automated Audit Report

Generates a structured text report including:

File metadata

Shape summary

Column standardization changes

ID protection decisions

Datatype decisions

Duplicate handling

Missing value strategy

Final validation status

Full action log

Ensures full transparency and governance traceability.

📊 Tested On

✔ 1M+ row Online Retail dataset
✔ HR Analytics dataset
✔ Multi-department Excel files
✔ Mixed-format CSV files

All passed integrity validation.

🛠 Tech Stack

Python

Pandas

NumPy

Regex

OpenPyXL

Data Profiling Logic

🏗 Design Philosophy

This project follows four principles:

Data Integrity First

No Silent Mutation

Dataset-Agnostic Logic

Business-Key Protection

📂 Output Files

After execution:

dataset_cleaned.xlsx

dataset_audit_report.txt

Both are automatically generated and downloadable (Colab supported).

🎯 Why This Project Matters

Most cleaning scripts:

Force datatype conversions

Break IDs

Ignore schema integrity

Provide no audit trail

This system prevents those issues and introduces enterprise-level control.
