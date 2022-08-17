# Database Structure

## Table Structure

### Users

Field | Type | Nullable | Unique | Default | Description
--- | --- | --- | --- | --- | ---
id | int | No | Yes | 0 | Primary Key
username | varchar(255) | No | Yes | NULL | Username
password | varchar(255) | No | No | NULL | Password (Encrypted)
email | varchar(255) | No | Yes | NULL | Email
phone_number | varchar(255) | Yes | Yes | NULL | Phone Number
created_at | datetime | No | No | NULL | Date Created
updated_at | datetime | No | No | NULL | Date Updated

### Accounts

Field | Type | Nullable | Unique | Default | Description
--- | --- | --- | --- | --- | ---
id | int | No | Yes | 0 | Primary Key
user_id | int | No | No | 0 | Foreign Key to Users Table
name | varchar(255) | No | No | "Account of {user}" | Name of the Account
initial_value | decimal(10,2) | No | No | 0 | Initial Value
description | varchar(255) | Yes | No | NULL | Description

### Categories

Field | Type | Nullable | Unique | Default | Description
--- | --- | --- | --- | --- | ---
id | int | No | Yes | 0 | Primary Key
user_id | int | No | No | No | Foreign Key to Users Table
name | varchar(255) | No | Yes | NULL | Name of the category

> Categories are used to categorize transactions and filter.
### Transactions

Field | Type | Nullable | Unique | Default | Description
--- | --- | --- | --- | --- | ---
id | int | No | Yes | 0 | Primary Key
account_id | int | No | No | 0 | Foreign Key to Accounts Table
value | decimal(10,2) | No | No | 0 | Value
type | Binary | No | No | 0 | Type of Transaction (0 - Payment, 1 - Entry)
efectuated_at | datetime | No | No | NULL | Date of Transaction
concept | varchar(255) | No | No | "" | Concept of the transaction
description | varchar(255) | Yes | No | NULL | Description
category | int | Yes | No | NULL | Category of the transaction (Foreign Key to Categories Table when not null)

### Registers

Field | Type | Nullable | Unique | Default | Description
--- | --- | --- | --- | --- | ---
id | int | No | Yes | 0 | Primary Key
account_id | int | No | No | 0 | Foreign Key to Accounts Table
value | decimal(10,2) | No | No | 0 | Value
date | datetime | No | NULL | No | Date when the register was created

> To keep track of the different states of the accounts during the time.