# Data Cleaning with Pandas

A Jupyter notebook demonstrating how to clean a customer call list with pandas.

## Repository files

- [Customer Call List.xlsx](Customer%20Call%20List.xlsx): input workbook.
- [Data Cleaning using Pandas.ipynb](Data%20Cleaning%20using%20Pandas.ipynb): cleaning workflow and saved outputs.
- [Data Cleaning using Pandas.html](Data%20Cleaning%20using%20Pandas.html): exported notebook for viewing without Jupyter.

## Run locally

1. Clone this repository and open a terminal in its folder.
2. Create and activate a virtual environment (recommended).
3. Install the notebook dependencies:

   ```sh
   python -m pip install pandas openpyxl notebook
   ```

4. Start Jupyter from the repository folder:

   ```sh
   python -m notebook
   ```

5. Open `Data Cleaning using Pandas.ipynb`. Before running it, replace the machine-specific path in the second cell with:

   ```python
   df = pd.read_excel("Customer Call List.xlsx")
   df
   ```

6. Restart the kernel and run all cells in order. The workbook must be in the notebook's working directory.

## Cleaning workflow

The notebook removes duplicate rows and `Not_Useful_Column`, trims selected punctuation from last names, removes phone-number separators and applies a `XXX-XXX-XXXX` format, and normalizes the `Paying Customer` and `Do_Not_Contact` fields. It also replaces selected missing-value text markers with empty strings.

## Current limitations

- Phone formatting uses string slicing; it does not validate phone numbers, country codes, or extensions. Review the results before using the list.
- `Do_Not_Contact` values are normalized, but the notebook does not filter out customers who should not be contacted.
- The notebook displays the cleaned DataFrame in memory; it does not save a cleaned file automatically.
- The HTML file contains saved output and is not automatically refreshed when the notebook changes.

## Export the result

After running the cleaning cells and reviewing `df`, add a final cell to save a separate workbook without overwriting the input:

```python
df.to_excel("Customer Call List Cleaned.xlsx", index=False)
```
