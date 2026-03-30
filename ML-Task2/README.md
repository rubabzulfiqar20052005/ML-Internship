# Task 2 — Sales Data Analyser

## Description
 Download or create a mock sales CSV with columns for product, 
region, date, quantity, and price. Write a Pandas script that loads the file, inspects it, 
filters for a specific region, adds a revenue column, groups by product to find total 
revenue, finds the top 5 products, merges with a mock product metadata table, and 
exports the final result to a new CSV. 

## Libraries Used
- **Pandas** — data loading, filtering, grouping, merging, export
- **NumPy** — random mock data generation

## Dataset
- **File:** `sales_data.csv` (mock dataset — generated in script)
- **Columns:** product, region, date, quantity, price
- **Rows:** 100

## Concepts & Functions Used
| Concept | Function |
|---------|---------|
| Load CSV | `pd.read_csv()` |
| Inspect data | `.head()`, `.dtypes`, `.describe()`, `.isnull()` |
| Filter by region | Boolean indexing — `df[df['region'] == 'North']` |
| Add revenue column | `df['revenue'] = quantity * price` |
| Group by product | `.groupby('product')['revenue'].sum()` |
| Sort and top 5 | `.sort_values().head(5)` |
| Merge with metadata | `pd.merge(..., on='product', how='left')` |
| Export to CSV | `.to_csv()` |

## Output Files
- `sales_data.csv` — original mock sales data
- `top5_products_north.csv` — final merged result (top 5 products, North region)
