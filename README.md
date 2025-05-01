# 🧹 SQL Data Cleaning & Standardization Project

This project focuses on improving data quality through SQL-based cleaning and standardization techniques. Using structured queries, we prepare a raw dataset for accurate and meaningful analysis.

## 🔧 Key Tasks Performed:
- ✂️ Trimming blank spaces
- 🔄 Fixing datatype inconsistencies
- 🗑️ Deleting irrelevant rows and columns
- 🧱 Handling NULL values

### Sample of SQL Queries used in the project :

- to find duplicates

```sql
WITH duplicate_cte AS
(
SELECT *,
ROW_NUMBER() OVER(
PARTITION BY company, industry, total_laid_off, percentage_laid_off, `date`) AS row_num
FROM layoffs_staging
)
SELECT *
FROM duplicate_cte
WHERE row_num > 1;
```





- STANDARDIZING DATA

```sql
SELECT DISTINCT company
FROM layoffs_staging2;

UPDATE layoffs_staging2
SET company = TRIM(company);
```
```sql
UPDATE layoffs_staging2
SET `date` = str_to_date(`date`, '%m/%d/%Y');
```

Every query in this project is crafted to enhance data integrity and ensure the dataset is fully analysis-ready.
