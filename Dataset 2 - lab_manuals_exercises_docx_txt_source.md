# Lab Manuals & Exercises — Adaptive Study & Lab Companion
**Format Target:** `.docx` or `.txt` Upload  
**Course Track:** Python Programming & Core Data Structures  

---

## Environment Setup Rules (Global Lab Standards)
1. **Runtime Environment:** Python 3.10 or higher. Verify version via `python --version` before executing lab scripts.
2. **Permitted Libraries:** Standard Library only (`math`, `statistics`, `collections`, `json`, `csv`). Third-party packages (`numpy`, `pandas`) are prohibited unless explicitly stated in the lab header.
3. **Code Style & Determinism:**
   - All functions must include docstrings and type annotations.
   - Do not use `input()` inside graded functions; accept all test inputs via function parameters.
   - Avoid global state mutation; each function must execute deterministically when called multiple times.
4. **Submission Naming:** Save each completed lab as `lab_<number>_<username>.py`.

---

## Lab 01: Safe List Filtering & Aliasing Prevention
**Problem_ID:** `LAB01-MUT`  
**Mapped Concept:** Topic 1 (Variables, References & Mutability) & Topic 2 (Definite Loops)

### 1. Lab Objectives
- Implement a non-destructive list cleaning function that preserves the caller's original dataset.
- Filter out sentinel error values and normalize valid numeric entries without mutating an active loop iterable.

### 2. Requirements & Constraints
- Write a function `sanitize_temperatures(raw_readings: list[float]) -> list[float]`.
- Remove any reading strictly below `-50.0` or strictly above `60.0` (sensor fault codes).
- Round each remaining valid reading to 1 decimal place.
- **Constraint:** The input list `raw_readings` must remain completely unchanged after the function returns.

### 3. Starter Code Template
```python
def sanitize_temperatures(raw_readings: list[float]) -> list[float]:
    """
    Return a new list containing valid temperatures between -50.0 and 60.0
    (inclusive), rounded to 1 decimal place. Must not mutate raw_readings.
    """
    # TODO: Initialize an empty result list
    
    # TODO: Iterate through raw_readings, filter out-of-bounds values,
    # and append rounded valid values to the result list
    
    pass


if __name__ == "__main__":
    sample_data = [21.45, -99.9, 18.22, 65.4, 22.09, -50.0]
    cleaned = sanitize_temperatures(sample_data)
    print("Original:", sample_data)
    print("Cleaned: ", cleaned)
```

### 4. Expected Output
```text
Original: [21.45, -99.9, 18.22, 65.4, 22.09, -50.0]
Cleaned:  [21.4, 18.2, 22.1, -50.0]
```

---

## Lab 02: Log Event Aggregation with Hash Maps
**Problem_ID:** `LAB02-DICT`  
**Mapped Concept:** Topic 3 (Dictionaries & Hash Table Lookup)

### 1. Lab Objectives
- Aggregate unstructured server log entries into a structured frequency dictionary in O(n) time.
- Handle missing dictionary keys safely without raising `KeyError`.

### 2. Requirements & Constraints
- Write a function `summarize_logs(log_lines: list[str]) -> dict[str, int]`.
- Each string in `log_lines` follows the format `"TIMESTAMP | LEVEL | MESSAGE"` (e.g., `"2026-11-23 08:15:00 | ERROR | Disk timeout"`).
- Extract the `LEVEL` token (stripped of surrounding whitespace) and count occurrences of each level.
- Return a dictionary mapping each uppercase log level to its integer count. If `log_lines` is empty, return `{}`.

### 3. Starter Code Template
```python
def summarize_logs(log_lines: list[str]) -> dict[str, int]:
    """
    Parse pipe-delimited log lines and return a frequency map of log levels.
    Format of each line: 'TIMESTAMP | LEVEL | MESSAGE'
    """
    level_counts: dict[str, int] = {}
    
    # TODO: Loop through log_lines
    # TODO: Split each line by '|' and extract the normalized LEVEL string
    # TODO: Increment count in level_counts safely
    
    return level_counts


if __name__ == "__main__":
    logs = [
        "2026-11-23 08:01:12 | INFO | Service started",
        "2026-11-23 08:02:45 | ERROR | Connection refused",
        "2026-11-23 08:03:10 | WARN | High memory usage",
        "2026-11-23 08:05:00 | ERROR | Retry limit exceeded",
    ]
    print(summarize_logs(logs))
```

### 4. Expected Output
```text
{'INFO': 1, 'ERROR': 2, 'WARN': 1}
```

---

## Lab 03: Gradebook Weighted Score Calculator
**Problem_ID:** `LAB03-FUNC`  
**Mapped Concept:** Topic 4 (Functions, Scope & Return Values)

### 1. Lab Objectives
- Compose pure helper functions that communicate exclusively via return values.
- Eliminate mutable default parameter bugs when building student records.

### 2. Requirements & Constraints
- Write `compute_weighted_grade(scores: list[float], weights: list[float]) -> float`.
- Validate that `len(scores) == len(weights)` and `len(scores) > 0`; otherwise raise `ValueError`.
- Validate that `sum(weights)` equals `1.0` within a tolerance of `1e-6`; otherwise raise `ValueError`.
- Return the weighted average rounded to 2 decimal places. Do not print inside the function.

### 3. Starter Code Template
```python
def compute_weighted_grade(scores: list[float], weights: list[float]) -> float:
    """
    Compute the weighted average of scores given matching weights summing to 1.0.
    Raises ValueError on mismatched lengths, empty inputs, or invalid weight sums.
    """
    # TODO: Validate input lengths and non-empty condition
    
    # TODO: Validate that weights sum to 1.0 (use abs(sum(weights) - 1.0) > 1e-6)
    
    # TODO: Compute weighted sum and return rounded to 2 decimal places
    pass


if __name__ == "__main__":
    student_scores = [88.0, 92.5, 79.0]
    syllabus_weights = [0.25, 0.35, 0.40]
    final_grade = compute_weighted_grade(student_scores, syllabus_weights)
    print(f"Weighted Grade: {final_grade}")
```

### 4. Expected Output
```text
Weighted Grade: 86.0
```