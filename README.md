# Excel-to-PostgreSQL-Table-Generator


## Overview

The **Excel-to-PostgreSQL Table Generator** is a versatile tool designed to simplify the process of converting data stored in Excel files into a PostgreSQL-compatible format. It automatically generates SQL `CREATE TABLE` statements based on the structure and data types found within the Excel file. Additionally, the tool exports the Excel data into a CSV file, which can then be easily imported into PostgreSQL.

This project addresses a common need for data migration, allowing users to quickly and accurately prepare their Excel data for use in a PostgreSQL database. The tool takes care of data type mapping, column name sanitization, and data export, making the process smooth and error-free.

## Features

### 1. **Automatic SQL Table Creation**
   - The tool reads the first 20 rows of an Excel file to infer data types and automatically generates a `CREATE TABLE` SQL statement. This statement can be directly used in a PostgreSQL environment to create a table that mirrors the structure of the Excel data.

### 2. **Column Name Sanitization**
   - Column names in Excel files often contain spaces, special characters, or formatting that are incompatible with SQL databases. The tool automatically sanitizes these column names by replacing spaces, hyphens, parentheses, and hashtags with underscores. This ensures that the generated SQL statement is valid and the column names are standardized.

### 3. **CSV Export**
   - Alongside generating the SQL statement, the tool also exports the Excel data into a CSV file. This CSV file is formatted with the sanitized column names, ensuring consistency between the table structure and the data being imported. The CSV file can be directly imported into the PostgreSQL table created with the generated SQL statement.

## Requirements

To run the **Excel-to-PostgreSQL Table Generator**, you will need the following:

- **Python 3.x**
- **Pandas**: A powerful data manipulation library used to read and process Excel files.
- **Openpyxl**: A library for reading and writing Excel files.

## Installation

### Step 1: Clone the Repository
Start by cloning the repository from GitHub and navigating into the project directory:

```bash
git clone https://github.com/yourusername/excel-to-postgresql.git
cd excel-to-postgresql
```

### Step 2: Install Required Python Packages
Install the necessary Python packages using pip:

```bash
pip install pandas
pip install openpyxl
```

These packages are essential for reading Excel files and processing the data for SQL conversion and CSV export.

## Usage

### Step 1: Prepare Your Excel File
Ensure that your Excel file is correctly formatted and ready for conversion. The tool is designed to read the first 20 rows of your Excel file to determine the data types of each column. If your file contains important data beyond the first 20 rows, you may want to modify the script to analyze a larger portion of the file.

### Step 2: Run the Script
To generate the SQL `CREATE TABLE` statement and export the data to a CSV file, you will need to provide the following inputs:

- **Table Name**: The name of the PostgreSQL table you wish to create. This name will be used in the generated SQL statement.
- **Excel File Path**: The path to your Excel file. The script will read this file and perform the necessary conversions.

### Step 3: Review the Output
After running the script:

- The tool will generate a SQL `CREATE TABLE` statement, which you can copy and paste into your PostgreSQL query tool. This statement defines the structure of the table based on the columns and data types detected in your Excel file.
- The tool will also export the Excel data to a CSV file with sanitized column names. This file is ready to be imported into the newly created PostgreSQL table.

### Step 4: Execute SQL in PostgreSQL
Use the generated SQL `CREATE TABLE` statement in your PostgreSQL database to create the table. After the table is created, you can import the CSV file into PostgreSQL using the appropriate data import commands.

## Example Use Case

Imagine you have an Excel file named `address.xlsx` that contains address-related data. You want to migrate this data into a PostgreSQL database under a table named `Airline`. By running the **Excel-to-PostgreSQL Table Generator**, you will receive:

- A SQL `CREATE TABLE` statement tailored to the structure of `address.xlsx`.
- A CSV file named `exported_dataframe.csv` that contains the data from the Excel file, formatted and sanitized for easy import into PostgreSQL.

The generated SQL might look something like this:

```sql
CREATE TABLE "Airline" (
    "address_id" INTEGER, 
    "address" VARCHAR, 
    "address2" REAL, 
    "district" VARCHAR, 
    "city_id" INTEGER, 
    "postal_code" REAL, 
    "phone" REAL, 
    "last_update" TIMESTAMP
);
```

You would then execute this SQL in PostgreSQL and import the `exported_dataframe.csv` file into the `Airline` table.

## Notes

- **Data Type Inference**: The tool infers data types based on the first 20 rows of the Excel file. If your data requires a broader analysis, consider modifying the script to read more rows.
- **Compatibility**: The tool ensures that the column names are compatible with PostgreSQL by sanitizing them. This prevents errors during SQL execution and data import.

## Contributing

Contributions are highly encouraged! Whether you have ideas for new features, optimizations, or bug fixes, feel free to fork the repository, make your changes, and submit a pull request. You can also open an issue on GitHub to report any problems or suggest improvements.

