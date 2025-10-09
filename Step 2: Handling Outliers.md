# Step 2: Handling Outliers ❗

<img width="690" height="251" alt="image" src="https://github.com/user-attachments/assets/645fc36c-e5d4-4870-99de-75acb12b84df" />

## 🔍 Initial Analysis on Outliers

By examining the differences between the minimum, maximum, and quartile values in the following columns, we can detect potential anomalies.

| Column Name | Observation | Potential Outliers According to IQR Rule |
| :--- | :--- | :--- |
| **capital-gain** 💸 | `max` = 99999.00 | **HIGHLY LIKELY OUTLIERS.** There is a huge difference between the maximum value (99999) and the 75th percentile (0.00). This indicates that the vast majority of the data is 0, but a tiny fraction reports extremely high gains. |
| **capital-loss** 📉 | `max` = 4356.00 | **HIGHLY LIKELY OUTLIERS.** Similar to `capital-gain`, the 75th percentile is 0, but the maximum value is quite high. |
| **fnlwgt** | `max` = 1.49M | **PROBABLE EXTREME VALUES.** The range between Min and Max is very wide. The maximum value is far from the mean (1.89e+05), suggesting the data is **right-skewed** and contains a few highly weighted records. |
| **age** | `min` = 17.00, `max` = 90.00 | **LOW PROBABILITY OF ERRORS.** The minimum (17) and maximum (90) ages are plausible for the dataset. However, how far the 90 value is from the 75th percentile (48) should be confirmed visually (Boxplot). |
| **hours-per-week** 🕒 | `min` = 1.00, `max` = 99.00 | **PROBABLE EXTREME VALUES.** Both the minimum (1 hour) and maximum (99 hours/week) are far from the mean (40.42) and the 25%-75% range (40-45 hours). 99 hours/week may be an outlier work duration. |

## Conclusion 💡

Specifically, since the **`capital-gain`** and **`capital-loss`** columns contain a few extremely high values while nearly all other data points are 0, these columns will require **outlier management** (either capping or transformation).

The next step should be to plot a **Boxplot** 📈 and determine thresholds using the **IQR method** to precisely detect these extreme values and protect your model.

This is the critical step of protecting your model from extreme values. Since the initial analysis confirmed that **`capital-gain`**, **`capital-loss`**, **`fnlwgt`**, and **`hours-per-week`** contain high-magnitude outliers, we will use the **IQR method** to implement a robust **capping (Winsorization)** strategy.

Here is the step-by-step solution in Python code, suitable for your Colab notebook.

## 🔨 Step 2: Handling Outliers (Capping Strategy)

### 1. Visualize Outliers (Boxplots) to Confirm 📈

First, let's visualize the most skewed features (`capital-gain` and `hours-per-week`) to confirm the extent of the outliers detected by `describe()`.


<img width="1349" height="416" alt="image" src="https://github.com/user-attachments/assets/5d591932-1300-459f-a139-f03239337376" />

### 2. Implement IQR Capping Function
We define a function to calculate the upper and lower bounds using the 1.5×IQR rule. For most of these financial columns (where values are 0), we only need to worry about the upper cap.

### 3. Apply Capping (Winsorization) to Numeric Features
We iterate through the identified columns and apply the capping strategy. This is a crucial step to preserve the high number of rows while mitigating the outlier's distorting effect.

<img width="379" height="106" alt="image" src="https://github.com/user-attachments/assets/bbd7e6bd-21fb-463e-82a4-69ac38529b5d" />

### 4. Verification

We check the descriptive statistics again to confirm that the maximum values for the capped columns are now equal to the calculated upper threshold, successfully completing Step 2.

<img width="315" height="102" alt="image" src="https://github.com/user-attachments/assets/5ed0736c-bc5a-44d6-90e6-67b7e3fada28" />


