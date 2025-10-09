# Step 1: Handling Missing Values ❓

<img width="308" height="584" alt="image" src="https://github.com/user-attachments/assets/fe6bb5a6-89ce-4489-888e-dd0ec604032a" />

<img width="287" height="488" alt="image" src="https://github.com/user-attachments/assets/c2ee640d-a5e6-4c11-8703-7a307bcd7eef" />

## 🔍 Step 1 Analysis: Missing Value Status

The output shows that three columns (`workclass`, `occupation`, and `native-country`) contain a significant number of missing values (NaN).

| Column Name | Missing Count | Data Type | Percentage ($\mathbf{n} \approx 32000$) | Action Decision |
| :--- | :--- | :--- | :--- | :--- |
| **workclass** | 963 | Categorical | $\approx 3.0\%$ | Imputation |
| **occupation** | 966 | Categorical | $\approx 3.0\%$ | Imputation |
| **native-country** | 274 | Categorical | $\approx 0.85\%$ | Imputation |
| **Other Columns** | 0 | Numeric/Categorical | $0\%$ | No Action Required |

### Strategy Rationale:

Since the percentage of missing data is low (max 3.0%), **Imputation** is preferred over dropping the rows to preserve the overall dataset size. As all affected columns are **Categorical**, the imputation strategy will involve either using the Mode or assigning a new **"Unknown"** category.

