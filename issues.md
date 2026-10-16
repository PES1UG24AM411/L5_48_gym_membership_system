# Static Code Analysis — Issues and Fixes

## Project
**File:** `gym_membership_system.py`

**Tools used:** Pylint, Bandit, and Flake8

## Issues identified and fixes applied

| No. | Tool | Issue identified | Fix applied |
|---:|---|---|---|
| 1 | Pylint | Missing function docstrings | Added docstrings to functions. |
| 2 | Pylint | Function names did not follow snake_case | Renamed functions to `register_member`, `cancel_membership`, `check_membership_status`, and `calculate_renewal_rate`. |
| 3 | Pylint | Mutable default argument (`member_log=[]`) | Changed the default to `None` and created/appended to a log only when one is provided. |
| 4 | Pylint | Unused imports and variables | Removed unused imports and variables. |
| 5 | Pylint / Flake8 | Incorrect comparison with `None` | Replaced `== None` with `is not None` in the membership check. |
| 6 | Pylint / Bandit | Unsafe use of `eval()` | Replaced expression evaluation with a numeric discount parameter and input validation. |
| 7 | Pylint / Bandit | Broad exception handling | Caught the specific `KeyError` in membership cancellation. |
| 8 | Bandit | MD5 used for member hashing | Replaced MD5 with SHA-256. |
| 9 | Bandit | Predictable random locker PIN | Replaced `random.randint()` with `secrets.randbelow()`. |
| 10 | Bandit | Shell command executed using `os.system()` | Removed the shell command and used a normal Python print statement. |
| 11 | Bandit | Hardcoded portal secret | Removed the hardcoded secret from the demonstration. |
| 12 | Pylint | File opened without a context manager or explicit encoding | Used `with open(..., encoding="utf-8")`. |
| 13 | Pylint | Parameter shadowed the global `members` variable | Renamed the parameter to `member_records`. |
| 14 | Flake8 | Long lines and formatting violations | Reformatted dictionaries and expressions across multiple lines. |
| 15 | Flake8 | Missing final newline | Added a final newline to the Python file. |
| 16 | Pylint | Unnecessary conditional return logic | Simplified the membership-status check into a Boolean expression. |

## Results

| Tool | Before | After |
|---|---|---|
| Pylint | 4.81/10 | 10.00/10 |
| Bandit | Security findings present, including high-severity findings | No issues identified |
| Flake8 | Multiple style and code-quality findings | No linting errors reported |

## Conclusion

Static code analysis helped identify maintainability, style, and security issues. The revised program uses clearer function names, safer input handling, stronger hashing, cryptographically secure PIN generation, and safer file handling. The final code achieved a Pylint score of 10.00/10, and Bandit reported no issues.
