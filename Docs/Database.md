# Database Structure

## Table Structure

### Users

Field | Type | Nullable | Default | Description
--- | --- | --- | --- | ---
id | int | No | 0 | Primary Key
username | varchar(255) | No | NULL | Username
password | varchar(255) | No | NULL | Password (Encrypted)
email | varchar(255) | No | NULL | Email
phone_number | varchar(255) | Yes | NULL | Phone Number
created_at | datetime | No | NULL | Date Created
updated_at | datetime | No | NULL | Date Updated

### Accounts

Field | Type | Nullable | Default | Description
--- | --- | --- | --- | ---
id | int | No | 0 | Primary Key
user_id | int | No | 0 | Foreign Key to Users Table
description | varchar(255) | Yes | NULL | Description
initial_value | decimal(10,2) | No | 0 | Initial Value

### Categories


Field | Type | Nullable | Default | Description
--- | --- | --- | --- | ---
id | int | No | 0 | Primary Key
name | varchar(255) | No | NULL | Name of the category

> Categories are used to categorize transactions and filter.
### Transactions

Field | Type | Nullable | Default | Description
--- | --- | --- | --- | ---
id | int | No | 0 | Primary Key
account_id | int | No | 0 | Foreign Key to Accounts Table
value | decimal(10,2) | No | 0 | Value
type | Binary | No | 0 | Type of Transaction (0 - Payment, 1 - Entry)
efectuated_at | datetime | No | NULL | Date of Transaction
concept | varchar(255) | No | "" | Concept of the transaction
description | varchar(255) | Yes | NULL | Description
category | int | No | 0 | Foreign Key to Categories Table

### Registers

Field | Type | Nullable | Default | Description
--- | --- | --- | --- | ---
id | int | No | 0 | Primary Key
account_id | int | No | 0 | Foreign Key to Accounts Table
value | decimal(10,2) | No | 0 | Value
date | datetime | No | NULL | Date when the register was created

> To keep track of the different states of the accounts during the time.