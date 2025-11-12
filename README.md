# Nashville Housing Dataset Cleaning

**Dataset Source / Inspiration:** [AlexTheAnalyst](https://www.youtube.com/@AlexTheAnalyst)  
**Database:** SQLite (DB Browser)  
**Project Type:** Data Cleaning / ETL  

---

## Project Overview

This repository contains a complete **data cleaning workflow** for the Nashville Housing dataset.  
The workflow is inspired by a tutorial from AlexTheAnalyst. The goal of this project is to prepare the dataset for analysis by standardizing dates, splitting addresses into separate columns, cleaning categorical values, and removing duplicates or unused columns.

---

## Files in this Repository

- `NashvilleHousing_Cleaning.sql` – SQLite script containing all cleaning steps (Steps 1–7).  
- `NashvilleHousing.csv` – Original dataset used for the project (optional, if included).  

---

## Cleaning Steps

1. **Inspect Raw Data**  
   - Previewed dataset and checked column types to understand inconsistencies.

2. **Standardize SaleDate**  
   - Ensured `SaleDate` is in ISO format (`YYYY-MM-DD`).  
   - No conversion was necessary as it was already standardized in Excel.

3. **Populate Missing PropertyAddress Data**  
   - Filled in `NULL` property addresses by referencing other rows with the same `ParcelID`.

4. **Split Property and Owner Addresses**  
   - `PropertyAddress` → `PropertySplitAddress` (Street), `PropertySplitCity` (City)  
   - `OwnerAddress` → `OwnerSplitAddress` (Street), `OwnerSplitCity` (City), `OwnerSplitState` (State)  
   - Removed trailing commas and spaces.

5. **Standardize SoldAsVacant Column**  
   - Converted `Y` → `Yes` and `N` → `No` for readability.

6. **Remove Duplicates**  
   - Eliminated duplicate rows based on `ParcelID`, `PropertyAddress`, `SalePrice`, `SaleDate`, `LegalReference`.  
   - Kept the first occurrence using `ROW_NUMBER()`.

7. **Delete Unused Columns**  
   - Removed original raw columns (`PropertyAddress`, `OwnerAddress`, `SaleDate`, `TaxDistrict`) to keep only cleaned data.

---

## How to Use

1. Open the `NashvilleHousing_Cleaning.sql` file in **DB Browser for SQLite** or any SQLite client.  
2. Execute the script step by step to clean the dataset.  
3. After execution, the `NashvilleHousing` table will be fully cleaned and ready for analysis.

---

## Notes

- This script is designed for **SQLite**, but can be adapted to SQL Server or other RDBMS with minor changes.  
- The dataset cleaning focuses on preparing the data for **analysis, visualization, or modeling**, ensuring all columns are standardized and duplicates removed.  
- Credit: Inspired by [AlexTheAnalyst](https://www.youtube.com/@AlexTheAnalyst) tutorial.

---

## License

This project is for educational purposes.

