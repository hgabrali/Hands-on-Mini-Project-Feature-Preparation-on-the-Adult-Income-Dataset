# Step 3: Handling Categorical Data 🏷️

* Find all the **categorical features** in the dataset.
* Convert them into **numeric form** so they can be used in models.
* Try both `pd.get_dummies()` and `OneHotEncoder`.
* Reflect: which method would you use in **production**, and why?

<img width="833" height="208" alt="image" src="https://github.com/user-attachments/assets/4c8adbf0-cbb7-4f02-bed1-ca9004019080" />

<img width="640" height="211" alt="image" src="https://github.com/user-attachments/assets/9d15f071-fb80-47d7-a67c-1d082b14afa6" />

<img width="912" height="291" alt="image" src="https://github.com/user-attachments/assets/bbc7a155-0c88-4651-8a19-454c9ef06349" />

<img width="640" height="421" alt="image" src="https://github.com/user-attachments/assets/72df65cf-a020-4988-9a6d-46cf7005d2be" />

## 🚀 Reflection: Production Choice

The **`OneHotEncoder`** from `sklearn.preprocessing` is **superior for production environments** because it can be integrated into a **pipeline** ⚙️.

Crucially, its **`handle_unknown='ignore'`** setting ensures the model won't crash when encountering a category (like a new `workclass` value) that wasn't seen during training. This stability is critical for real-world deployment.
