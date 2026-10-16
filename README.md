# Lab 5: Static Code Analysis — Gym Membership System

## 1. Project Overview

The Gym Membership System is a Python program for managing gym memberships. It supports member registration, membership cancellation, membership status checks, renewal fee calculations, member identifier hashing, locker PIN generation, and roster export.

The objective of this lab is to use **Pylint, Bandit, and Flake8** to identify and fix code quality, style, and security issues.

## 2. Tools Used

- **Pylint:** Identifies code quality, naming, documentation, and maintainability issues.
- **Bandit:** Detects potential security vulnerabilities in Python code.
- **Flake8:** Checks Python code for style violations and common programming errors.

## 3. Issues Identified and Fixes Applied

| Issue | Type | Fix Applied |
|---|---|---|
| Unsafe use of `eval()` | Security — Bandit | Replaced expression evaluation with a numeric discount parameter and validation. |
| MD5 hashing | Security — Bandit | Replaced MD5 with SHA-256 for member identifier hashing. |
| Predictable locker PIN generation | Security — Bandit | Replaced `random.randint()` with `secrets.randbelow()`. |
| Shell command execution using `os.system()` | Security — Bandit | Removed shell execution and used a Python print statement. |
| Hardcoded portal secret | Security — Bandit | Removed the hardcoded secret from the demonstration. |
| Mutable default argument | Code quality — Pylint | Changed `member_log=[]` to `member_log=None`. |
| Broad exception handling | Code quality — Pylint | Replaced the bare `except` with a specific `KeyError` handler. |
| Missing function docstrings | Code quality — Pylint | Added docstrings to functions. |
| Inconsistent function naming | Style — Pylint | Renamed functions to follow `snake_case`. |
| Incorrect comparison with `None` | Style — Flake8 | Used an identity comparison. |
| Unsafe file handling | Code quality — Pylint | Used a context manager and specified UTF-8 encoding. |
| Unused imports and variables | Code quality — Pylint / Flake8 | Removed unused imports and variables. |
| Long lines and missing final newline | Style — Flake8 | Reformatted the code and added a final newline. |

The complete issue table, including line numbers and descriptions, is maintained in `issues.md`.

## 4. Changes Made to the Program

1. Renamed functions to improve consistency and readability.
2. Added documentation strings to explain function responsibilities.
3. Improved member registration by avoiding a mutable default argument.
4. Simplified membership status checking.
5. Added validation for renewal discounts, including type and range checks.
6. Replaced unsafe dynamic expression evaluation with normal arithmetic.
7. Updated member identifier hashing from MD5 to SHA-256.
8. Used Python's `secrets` module for locker PIN generation.
9. Removed shell-command execution from roster export.
10. Improved file handling using `with open()` and UTF-8 encoding.
11. Removed unused imports, variables, and the hardcoded demonstration secret.
12. Added a main-entry-point guard to prevent the demonstration from running automatically when the module is imported.

## 5. Static Analysis Results

| Tool | Before | After |
|---|---|---|
| Pylint | 4.81/10 | 10.00/10 |
| Bandit | Security findings detected, including high-severity findings | No issues identified |
| Flake8 | Multiple style and code-quality findings | No linting errors reported |

The final Pylint score increased by **5.19 points**, from 4.81/10 to 10.00/10.

## 6. How to Run the Program

Activate the virtual environment if it is not already active:

```bash
source venv/bin/activate
```

Install the required analysis tools:

```bash
pip install pylint bandit flake8
```

Run the program:

```bash
python gym_membership_system.py
```

Run the static analysis tools:

```bash
pylint gym_membership_system.py
bandit -r gym_membership_system.py
flake8 gym_membership_system.py
```

Save reports for comparison:

```bash
pylint gym_membership_system.py > pylint_report_after.txt 2>&1
bandit -r gym_membership_system.py > bandit_report_after.txt 2>&1
flake8 gym_membership_system.py > flake8_report_after.txt 2>&1
```

## 7. Project Files

- `gym_membership_system.py` — Cleaned Python implementation.
- `issues.md` — Issues identified, their types, line numbers, descriptions, and fixes.
- `reflection.md` — Answers to the lab reflection questions.
- `pylint_report_before.txt` and `pylint_report_after.txt` — Pylint results before and after fixes.
- `bandit_report_before.txt` and `bandit_report_after.txt` — Bandit results before and after fixes.
- `flake8_report_before.txt` and `flake8_report_after.txt` — Flake8 results before and after fixes.

## 8. Conclusion

This lab demonstrated how static code analysis can improve Python code quality, readability, maintainability, and security. By applying the recommendations from Pylint, Bandit, and Flake8, the program achieved a Pylint score of 10.00/10, no reported Bandit issues, and no Flake8 linting errors.

The exercise also highlighted the importance of validating inputs, avoiding unsafe operations, handling exceptions precisely, and following consistent coding standards.
