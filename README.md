# Telecom-Data-Migration-ETL-Mosul
A scalable ETL pipeline designed to clean, validate, and migrate telecom customer data (e.g., billing records, network usage, subscriptions) from legacy systems to a modern platform. Ensures data integrity, compliance with telecom standards, and seamless integration with downstream analytics tools.  

## 📌 Overview
This project is designed to **migrate customer and device data from the old system to the new system** for a telecom service provider operating in Mosul, Iraq. The migration process ensures data accuracy, consistency, and integrity while transferring **customer subscriptions, device specifications, service statuses, package details, and financial records**.

The SQL scripts included in this repository extract, clean, and load data into the new system, enabling seamless transition without data loss or inconsistencies.

## 🚀 Key Features
- **Data Extraction & Cleansing**: Extract relevant telecom customer data while filtering out test and invalid records.
- **Customer & Device Management**: Categorize **CPE (Customer Premises Equipment) and Mifi** devices based on model, serial number, and customer subscription.
- **Package Mapping & Optimization**: Ensure correct mapping of **commercial, FNF (Friends & Family), test, and promotional** packages.
- **Localization Support**: Assign Arabic and Kurdish language preferences based on customer data.
- **Financial Data Migration**: Transfer customer **wallet balances (IQD) and loyalty points** accurately.
- **Data Integrity & Validation**: Ensure only valid and active records are migrated.
- 
## 🛠️ Migration Process
### 1️⃣ `extract_mosul.sql`
- **Purpose**: Extracts relevant customer and device data from the old telecom system.
- **Operations**:
  - Joins multiple tables to fetch complete customer profiles.
  - Filters data to include only active and valid subscriptions.
  - Formats and trims data for uniformity.

### 2️⃣ `mosul.sql`
- **Purpose**: Cleans and transforms the extracted data before inserting it into the new system.
- **Operations**:
  - Maps **old system package codes** to new system equivalents.
  - Validates customer subscription and device details.
  - Ensures correct financial and package information before insertion.

## 🔑 Key Components
### Tables Involved
- **`vu_simcards`** → SIM card details (ICCID, IMSI, MAC addresses).
- **`vu_subscriptions`** → Customer subscription statuses (active, blocked, canceled).
- **`vu_subs_packages`** → Package codes and types (e.g., "basic," "super," "premium").
- **`vu_ic_items`** → Device models and specifications.
- **`vu_cust_wallet`** → Customer wallet balances and transactions.

### Migrated Data Fields
- **Device Details**: `serial_number`, `mac`, `product_class`
- **Customer Info**: `full_name`, `mobile_number`, `email`, `preferred_language`
- **Service Metrics**: `status`, `provisioned_at`, `activated_at`, `subscription_expiry`
- **Financials**: `iqd` (wallet balance in Iraqi Dinar), `maxmize_points` (loyalty points)
- **Metadata**: `updated_by`, `updated_at`


