# Algorithmic Investment Banking Model & DCF Valuation Pipeline

## Overview
This project is an end-to-end Python pipeline that automates the construction of a Wall Street-grade, fully linked 3-statement financial model and Discounted Cash Flow (DCF) valuation. 

By integrating live market data via the `yfinance` API, the script cleans historical SEC filings, maps them to a standardized Chart of Accounts, and algorithmically generates a dynamic Excel workbook (`.xlsx`) using `openpyxl`. The resulting model includes an automated debt sweep, CAPM WACC derivation, and a formula-driven sensitivity matrix.

## Key Features
* **Live Data Ingestion:** Automates the extraction of historical Income Statements, Balance Sheets, and Cash Flow Statements using `pandas` and `yfinance`.
* **Dynamic 3-Statement Engine:** Programmatically links the core financial statements with explicit balance sheet checks to guarantee accounting integrity ($Assets - Liabilities - Equity = 0$).
* **Advanced Capital Structure:** Implements a Debt Schedule with an automated cash sweep mechanism, intelligently circumventing circular references by calculating interest on beginning debt balances.
* **Rigorous DCF Valuation:**
  * Derives Cost of Equity dynamically using the Capital Asset Pricing Model (CAPM).
  * Calculates intrinsic value using a blended average of the **Perpetuity Growth (Gordon Growth)** and **Exit Multiple (EV/EBITDA)** methodologies.
* **Sensitivity Analysis:** Generates a robust 5x5 formula-driven matrix to stress-test the implied share price against fluctuations in WACC and Terminal Growth Rates.
* **Automated Executive Summary:** Compares the dynamically calculated DCF target price against live market quotes to programmatically issue an investment recommendation (Strong Buy, Buy, Hold, Sell).

## Tech Stack
* **Language:** Python
* **Libraries:** `pandas` (Data manipulation), `yfinance` (Market data API), `openpyxl` (Excel automation & formula injection)

## Installation & Usage
1. Clone the repository.
2. Install the required dependencies:
   ```bash
   pip install pandas yfinance openpyxl

3. Run the Jupyter Notebook (TSCO_Financial_Model_Tutorial.ipynb) to execute the pipeline.

4. Important: Open the generated TSCO_Final_IB_Model.xlsx file in Microsoft Excel and click "Enable Editing" (or press F9) to initialize Excel's calculation engine and populate the cached formula values.
