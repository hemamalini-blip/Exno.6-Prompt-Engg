# Exno.6-Prompt-Engg
# Name:Hemamalini S
# Register no:212222210006
# Aim: Development of Python Code Compatible with Multiple AI Tools

---

## **Algorithm**

1. **Input Stage:**

   * Accept a file path from the user.
   * Automatically detect the file type using its extension (`.csv` or `.json`).

2. **Processing Stage:**

   * If the file is `.csv`:

     * Use the built-in `csv` module and `DictReader()` to convert rows into dictionaries.
   * If the file is `.json`:

     * Use the built-in `json` module to load the JSON data.
     * Ensure consistency by converting a single JSON dictionary into a list.

3. **Error Handling:**

   * If the file is not `.csv` or `.json`, raise an appropriate error message.

4. **Output Stage:**

   * Return a **list of dictionaries** that represents the file content.
   * This standardized format ensures smooth compatibility with multiple AI tools.

---

## **Program (Python Code)**

```python
import csv
import json
import os

def read_file_to_dicts(file_path):
    """
    Reads a CSV or JSON file and returns a list of dictionaries.
    Supports .csv and .json file formats.
    """
    _, ext = os.path.splitext(file_path)
    ext = ext.lower()
    
    data = []
    
    if ext == ".csv":
        with open(file_path, mode="r", encoding="utf-8") as f:
            reader = csv.DictReader(f)
            data = [row for row in reader]
            
    elif ext == ".json":
        with open(file_path, mode="r", encoding="utf-8") as f:
            data = json.load(f)
            # Ensure single dictionary is wrapped as a list
            if isinstance(data, dict):
                data = [data]
    
    else:
        raise ValueError("Unsupported file format. Please provide .csv or .json")
    
    return data


# Example Usage:
# csv_data = read_file_to_dicts("sample.csv")
# json_data = read_file_to_dicts("sample.json")
```

---

## **Workflow Diagram**

```
        ┌────────────────────┐
        │   Input: File Path │
        └─────────┬──────────┘
                  │
       ┌──────────▼───────────┐
       │ Detect File Extension│
       └──────────┬───────────┘
                  │
   ┌──────────────▼───────────────┐
   │ If .csv → Use csv.DictReader │
   └──────────────┬───────────────┘
                  │
   ┌──────────────▼───────────────┐
   │ If .json → Use json.load     │
   │ Convert dict → list if needed│
   └──────────────┬───────────────┘
                  │
       ┌──────────▼───────────┐
       │ Return List of Dicts │
       └──────────────────────┘
```

---

## **Sample Input and Output**

### **Case 1: CSV Input**

**Input File (`sample.csv`):**

```
name,age,city
Alice,25,London
Bob,30,New York
```

**Output (Python List of Dictionaries):**

```python
[
  {"name": "Alice", "age": "25", "city": "London"},
  {"name": "Bob", "age": "30", "city": "New York"}
]
```

---

### **Case 2: JSON Input**

**Input File (`sample.json`):**

```json
[
  {"name": "Alice", "age": 25, "city": "London"},
  {"name": "Bob", "age": 30, "city": "New York"}
]
```

**Output (Python List of Dictionaries):**

```python
[
  {"name": "Alice", "age": 25, "city": "London"},
  {"name": "Bob", "age": 30, "city": "New York"}
]
```

---

## **Discussion**

* This function standardizes the data format for **AI applications**.
* AI models often require structured input (JSON-like objects). By unifying `.csv` and `.json` into a **list of dictionaries**, developers can seamlessly:

  * Automate API interactions.
  * Compare outputs across tools.
  * Generate actionable insights from structured datasets.
* This ensures **compatibility and scalability** in real-world AI pipelines.


# Result: The corresponding Prompt is executed successfully
