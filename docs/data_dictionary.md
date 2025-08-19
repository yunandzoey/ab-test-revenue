# Data Dictionary

| Column       | Type   | Description                              |
|--------------|--------|------------------------------------------|
| user_id      | string | Unique user                               |
| variant_name | string | Raw variant label (control/treatment)     |
| revenue      | float  | Revenue in test window                    |
| date         | date?  | Optional event date                       |

**Derived:**  
- `arm`: 'A'/'B' from variant_name  
- `converted`: 1 if revenue>0 else 0

**Analytic export:** `user_id,arm,converted,revenue`  
**BI summary export:** `metric,arm,value,ci_low,ci_high,p_value`
