# Personal-Finance
A project to showcase data analysis skills, analyzing my spending across multiple accounts from 02-2025 to 02-2026
Data files are not included in this repository to protect personal information.

## Scope
Utilize Google Sheets to analyze personal spending habits to discover actionable insights and facilitate change

## Phase 1 - Google Sheets Analysis

### Obtaining Data
* Download statements from credit lenders and bank accounts as .CSV files
  * Set date range for 02-2025 to 02-2026
* Convert .CSV files into separate Google Sheets
* Create a Master Google Sheet document with 5 internal sheets
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
* In monthly_summary, create a pivot table with range `raw_data!B1:H756`
  * Rows = my_category
  * Columns = date
  * Values = amount
* Format all money values as currency

<img width="2556" height="445" alt="image" src="https://github.com/user-attachments/assets/87b5eb57-d2a6-410a-bb4f-5674f3fa75c3" />

Table 2 - Spending by Source 
* Sources: Bank 1, Bank 2, Card 1, Card 2
  * Represent real bank or card accounts
* In monthly_summary, create a second pivot table with range `raw_data!B1:H756`
  * Rows = source
  * Values = sum of amount
  * Values = count of amount
    * Considered amount of transactions
* Format sum of amount as currency

<img width="538" height="206" alt="image" src="https://github.com/user-attachments/assets/fabc1f03-10d4-4797-b65a-a02480e3dcdb" />

Table 3 - Top 10 Merchants
* Used a formula for this because sorting the pivot table did not work the way I needed
  * Formula: `=QUERY(raw_data!B:E, "select C, sum(D) where C is not null group by C order by sum(D) desc limit 10 label C 'Merchant', sum(D) 'Total Spent'")`

<img width="494" height="402" alt="image" src="https://github.com/user-attachments/assets/0d2ebef1-f1a6-41a5-8997-d1b188087023" />

### Insights
1. What is the highest spending category?
   * Bills

2. Is my spending trending up or down?
   * Trending downward overall

3. Which months were most expensive and why?
   * March is the most expensive, followed by February. January data appears to be missing which could skew findings.
   * March is the most expensive from taking a road trip





















