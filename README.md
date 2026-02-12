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
   * categories - Mapping of my categories
   * dashboard - Contains dashboards to visually analyze data and findings
   * monthly_summary - Monthly analysis of findings
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

### Creating Pivot Tables

### Building Dashboards

### Insights
1. What is the highest spending category?

2. Is my spending trending up or down?

3. Which months were most expensive and why?

4. Where am I over budget?

5. What is one specific action I could take to save money?



## Phase 2 - Python Automation and Forcasting






















