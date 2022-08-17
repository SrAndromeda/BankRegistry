## API Endpoints

> The API only take care of providing the information, All the logic is done in the frontend, this is because the  DataBase is only intended for consistency and syncronization between devices.

---

## User

### /user/login

- Method: POST
- Description: Login a user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    username | string | true | The username of the user
    password | string | true | The password of the user

### /user/register

- Method: POST
- Description: Register a user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    username | string | No | The username of the user
    password | string | No | The password of the user
    email | string | No | The email of the user
    phone_number | string | Yes | The phone number of the user

### /user/{id}

- Method: GET
- Description: Get the user information

### /user/{id}

- Method: PATCH
- Description: Update the user information
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    username | string | Yes | The username of the user
    password | string | Yes | The password of the user
    email | string | Yes | The email of the user
    phone_number | string | Yes | The phone number of the user

### /user/{id}

- Method: DELETE
- Description: Delete the user


---

## Accounts

### /accounts

- Method: GET
- Description: Returns all the accounts of the user

### /accounts

- Method: POST
- Description: Creates a new account for the user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    name | string | No | Name of the Account
    initial_value | float | No | Initial Value
    description | string | Yes | Description

- Returns: The new account created
    Parameter | Type | Description
    --------- | ---- | -----------
    id | int | Id of the account
    user_id | int | Id of the owner of the account
    name | string | Name of the Account
    initial_value | float | Initial Value
    description | string | Description

### /accounts/{id}

- Method: GET
- Description: Returns the account with the id provided

### /accounts/{id}

- Method: PATCH
- Description: Updates the account with the id provided
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    name | string | Yes | Name of the account
    initial_value | float | Yes | Initial Value
    description | string | Yes | Description

### /accounts/{id}

- Method: DELETE
- Description: Deletes the account with the id provided (Also all the transactions and registers of the account)

---

## Categories

### /categories

- Method: GET
- Description: Returns all the categories of the user

### /categories

- Method: POST
- Description: Creates a new category for the user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    name | string | No | NULL | Name of the category

- Returns: The new category created

    Parameter | Type | Description
    --------- | ---- | -----------
    id | int | Id of the category
    user_id | int | Id of the owner of the category
    name | string | Name of the category

### /categories/{id}

- Method: GET
- Description: Returns the category with the id provided

### /categories/{id}

- Method: PATCH
- Description: Updates the category with the id provided
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    name | string | Yes | Name of the category

### /categories/{id}

- Method: DELETE
- Description: Deletes the category with the id provided
---

## Transactions

### /transactions

- Method: GET
- Description: Returns all the transactions for the user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    account_id | int | Yes | Id of the account
    category_id | int | Yes | Id of the category
    start_date | date | Yes | Start date of the transactions
    end_date | date | Yes | End date of the transactions
    description | string | Yes | Description of the transactions
    type | string | Yes | Type of the transactions
    start_value | float | Yes | Initial value of the transactions
    end_value | float | Yes | End value of the transactions

### /transactions/{id}

- Method: POST
- Description: Creates a new transaction for the user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    account_id | int | No | Account id of the transaction
    value | float | No | Value
    type | Binary | No | Type of Transaction (0 - Payment, 1 - Entry)
    efectuated_at | datetime | No | Date of Transaction
    concept | float | No | Concept of the transaction
    description | string | Yes | Description
    category | int | Yes | Category id of the transaction 

- Returns: The new transaction created

### /transactions/{id}

- Method: GET
- Description: Returns the transaction with the id provided

### /transactions/{id}

- Method: PATCH
- Description: Updates the transaction with the id provided
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    account_id | int | Yes | Account id of the transaction
    value | float | Yes | Value
    type | Binary | Yes | Type of Transaction (0 - Payment, 1 - Entry)
    efectuated_at | datetime | Yes | Date of Transaction
    concept | float | Yes | Concept of the transaction
    description | string | Yes | Description
    category | int | Yes | Category id of the transaction

- Returns: The updated transaction

### /transactions/{id}

- Method: DELETE
- Description: Deletes the transaction with the id provided

---

## Registers

### /registers

- Method: GET
- Description: Returns all the registers for the accounts owned by the user
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    account_id | int | Yes | Id of the account
    start_date | date | Yes | Start date of the registers
    end_date | date | Yes | End date of the registers
    start_value | float | Yes | Initial value of the registers
    end_value | float | Yes | End value of the registers

### /registers/{id}

- Method: GET
- Description: Returns the register with the id provided

### /registers

- Method: PUT
- Description: Updates the registers that satisfy the parameters provided (All can not be null, at least one must be provided)
- Parameters:

    Parameter | Type | Nullable | Description
    --------- | ---- | -------- | -----------
    id | int | Yes | Id of the register
    start_date | date | Yes | Start date of the registers
    end_date | date | Yes | End date of the registers

> This method update the registers with the transactions in the configured interval on the server

- Returns: The updated register