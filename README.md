# ☕ Cafe Sales Data Cleaning (Excel Project)

This project showcases practical Excel-based data cleaning on a real-world cafe sales dataset. The data contained missing values, unknown labels, and inconsistent records. All cleaning was done using Excel formulas — no external tools or scripts.

---

## 📌 Project Objective

To clean and structure messy sales data using only **Microsoft Excel and Google Sheets**, preparing it for downstream analysis.

---

## 📂 Files Included

| File Name                         | Description                                      |
|----------------------------------|--------------------------------------------------|
| `dirty_cafe_sales.csv`           | Raw dataset with missing, unknown, and blank values |
| `Cleaned_cafe_sales_data.csv`    | Fully cleaned dataset (final version)            |
| `Cafe_Sales_Cleaned_AdityaV.xlsx`| Excel file with structured sheets: Raw, Cleaned, Log |

---

## 🧼 Cleaning Steps Performed

| Step | Column Affected      | Description                                                                 |
|------|----------------------|-----------------------------------------------------------------------------|
| 1    | All Columns          | Deleted rows where **all columns were blank**                               |
| 2    | Item, Location, Payment_Method | Replaced `"UNKNOWN"` with blank (`""`) to remove placeholder noise       |
| 3    | Price_Per_Unit       | Filled missing values using **Item–Price mapping**                          |
| 4    | Item                 | Inferred missing item names using **Price_Per_Unit**                        |
| 5    | Total_Spent          | Calculated missing values using: `Quantity × Price_Per_Unit`               |
| 6    | General              | Removed all formulas and pasted cleaned values for final delivery           |
| 7    | Formatting           | Cleaned up column formatting (text, numbers, currency, alignment)           |

---

## 💸 Item–Price Mapping Used

| Item      | Price |
|-----------|-------|
| Sandwich  | 4     |
| Coffee    | 2     |
| Cake      | 3     |
| Cookie    | 1     |
| Salad     | 5     |
| Smoothie  | 4     |
| Juice     | 3     |
| Tea       | 1.5   |

---

## 🧠 Key Excel Formulas Used

### 🔹 Fill missing `Price_Per_Unit` from `Item`:
```excel
=IF(B2="", "", SWITCH(B2,
  "Sandwich", 4,
  "Coffee", 2,
  "Cake", 3,
  "Cookie", 1,
  "Salad", 5,
  "Smoothie", 4,
  "Juice", 3,
  "Tea", 1.5,
  ""))

### To fill missing Item based on Price_Per_Unit:

=IF(OR(B2="", B2="UNKNOWN"),
  IF(D2=1.5, "Tea",
  IF(D2=2, "Coffee",
  IF(D2=1, "Cookie",
  IF(D2=5, "Salad",
  IF(D2=4, "Sandwich",
  IF(D2=3, B2, B2))))),
  B2)

### To calculate Total_Spent only if Quantity and Price are available:

=IF(AND(ISNUMBER(C2), ISNUMBER(D2)), C2 * D2, "")

