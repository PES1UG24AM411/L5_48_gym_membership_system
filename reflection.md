# Reflection — Static Code Analysis

## 1. What did I learn from this lab?

I learned how to use Pylint, Bandit, and Flake8 to identify different categories of problems in Python code. Pylint helped improve code quality and maintainability, Bandit identified potential security risks, and Flake8 highlighted style and formatting issues.

## 2. What were the main problems in the original program?

The original program contained unsafe expression evaluation with `eval()`, use of MD5 hashing, predictable random PIN generation, shell-command execution, a hardcoded secret, a mutable default argument, and broad exception handling. It also contained naming, documentation, and formatting issues.

## 3. How did I improve the program?

I replaced unsafe expression evaluation with a validated numeric discount, used SHA-256 for member identifier hashing, generated PINs with Python's `secrets` module, removed shell-command execution, improved exception handling, and used a context manager for file operations. I also corrected naming and formatting issues and added function docstrings.

## 4. What were the final analysis results?

Pylint improved from 4.81/10 to 10.00/10. Bandit reported no issues in the final scan, and Flake8 produced no linting errors.

## 5. Why is static code analysis important?

Static code analysis can detect potential problems before a program is deployed or executed in production. It improves readability, consistency, maintainability, and security. Using multiple tools is valuable because each tool focuses on different types of problems.

## 6. What would I improve further?

I would add a dedicated automated test suite, validate membership data more thoroughly, and use a proper secret-management mechanism if the application later integrates with a real portal. I would also review the design before using the program with real membership or personal data.
