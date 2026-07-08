# Exclusions Database

This project builds a structured database for healthcare provider exclusion records from multiple sources, including the HHS-OIG exclusion list and the Georgia DCH OIG exclusion list.

The goal of this project is to clean raw exclusion data, organize it into a relational database, and make the records easier to search, manage, and analyze.

## Project Overview

Healthcare exclusion lists contain individuals or businesses that are excluded from participating in certain healthcare programs. Different sources often provide different columns and formats, so this project creates a consistent database structure that can handle data from multiple sources.

This project includes:

- Data cleaning with Python and Pandas
- A relational database design for excluded parties
- PostgreSQL as the database system
- Prisma for schema definition and database migration
- pgAdmin for viewing and managing the database
- CSV files for cleaned/imported data

## Data Sources

The database is designed around exclusion data from:

- HHS-OIG exclusion list
- Georgia DCH OIG exclusion list

These sources do not always contain the same fields. For example, one source may include individual names, while another may mainly include business or organization names. Some fields such as NPI, UPIN, specialty, address, exclusion type, and reinstatement date may also be missing depending on the source.

## Database Structure

The main tables include:

### `sources`

Stores information about each data source, such as the source name, file name, and source type.

### `import_logs`

Tracks each import process, including when data was imported and how many records were added.

### `parties`

Stores the excluded party information. A party can be either an individual or a business.

Examples:

- Individual: first name, last name, middle name
- Business: business name

### `identifiers`

Stores identifiers connected to each party, such as NPI, UPIN, or other ID values when available.

### `exclusions`

Stores exclusion-related information, such as exclusion type, specialty, exclusion date, reinstatement date, waiver date, and status.

## Technologies Used

- Python
- Pandas
- PostgreSQL
- Prisma
- SQL
- pgAdmin

## Project Files

```text
clean.py              # Cleans and prepares raw data
seed.py               # Imports cleaned data into the database
schema.prisma         # Defines the database models and relationships
migration.sql         # SQL generated from Prisma migration
exclusions.csv        # Cleaned exclusion records
identifiers.csv       # Identifier records such as NPI or UPIN
parties.csv           # Excluded individual or business records
sources.csv           # Source metadata
import_logs.csv       # Import tracking information
