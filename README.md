# Personal-Finance
A project to showcase data analysis skills, analyzing my spending across multiple accounts from 02-2025 to 02-2026 (exclusive)

## Scope
Utilize Google Sheets to analyze personal spending habits to discover actionable insights and facilitate change


## Phase 1 - Google Sheets Analysis

### Obtaining Data
* Download statements from credit lenders and bank accounts as .CSV files
  * Set date range for 02-2025 to 02-2026
* Convert .CSV files into separate Google Sheets
* Create a Master Google Sheet document with 4 internal sheets
   * raw_data - Raw data from all sources to be processed
   * dashboard - Contains dashboards to visually analyze data and findings
   * monthly_summary - Monthly analysis of findings
   * categories - Mapping of my categories
   * lookup_table - Contains the lookup table for custom categorization
* Copy specific fields from each sheet into the raw_data sheet
  * Fields:
    * date - Date of transaction
    * merchant - Name of merchant who received payment
    * amount - Total amount of the transaction
    * original_category - What credit lender/bank labeled the transaction as
    * my_category - What I consider the transaction to be
    * source - Which credit lender or bank account
    * notes - Anything extra
   
### Category System
* Within the categories sheet
  * Fields:
    * my_category - The category name that I came up with
    * description - A description defining what types of transactions fit into which category
    * budget_monthly - Monthly spending allocation

### Data Cleaning
* Utilize filtering to search for and remove the following:
  * Remove positive income transactions
    * Paychecks
    * Venmo cashout
    * Transfers between bank accounts
  * Remove credit card payments

### Categorizing Transactions
* Use a custom function that utilizes a lookup table for ease of use and scaling
  * Categories:
    * Groceries
    * Dining Out
    * Transportation
    * Subscriptions
    * Travel
    * Bills
    * Entertainment
    * Shopping
    * Other
* Utilize filtering of original_category, sorting merchant from A-Z to categorize one category at a time
* Once most items have been categorized, set a filter on my_category to find all FALSE values to determine which merchants still need to be categorized

### Creating Pivot Tables
Table 1 - Monthly Spending by Category
* Modify dates of transactions to make them compatible with a pivot table
  * Insert a new row B and use the formula `=TEXT(A2,"yyyy-mm")` to change the format into text with the structure of yyyy-mm
* In monthly_summary, create a pivot table with range `raw_data!B1:H586`
  * Rows = my_category
  * Columns = date
  * Values = amount
* Format all money values as currency

Table 2 - Spending by Source (Apple Card, Discover Card, Bank Account)
* In monthly_summary, create a second pivot table with range `raw_data!B1:H586`
  * Rows = source
  * Values = sum of amount
  * Values = count of amount
    * Considered amount of transactions
* Format sum of amount as currency

Table 3 - Top 10 Merchants
* Used a formula for this because sorting the pivot table did not work the way I needed
  * Formula: `=QUERY(raw_data!B:E, "select C, sum(D) where C is not null group by C order by sum(D) desc limit 10 label C 'Merchant', sum(D) 'Total Spent'")`

### Building Dashboards

### Insights
1. What is the highest spending category?

2. Is my spending trending up or down?

3. Which months were most expensive and why?

4. Where am I over budget?

5. What is one specific action I could take to save money?



## Phase 2 - Python Automation and Forcasting






















