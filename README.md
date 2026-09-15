# Bank Management System

A **console-based Bank Management System** built with **C++**.

The application simulates a basic banking environment where authorized users can manage client accounts, perform transactions, and manage system users through a menu-driven command-line interface.

Client and user data is stored in text files, allowing the application to preserve its data between runs.

---

## Features

### Client Management

The system provides several operations for managing bank clients:

- Show all clients
- Add new clients
- Update existing client information
- Delete clients
- Find a client by account number
- Prevent duplicate account numbers
- Display client account details

Each client contains:

- Account number
- PIN code
- Name
- Phone number
- Account balance

---

### Transactions

Users with the required permission can access the transaction menu to perform banking operations.

Available transactions:

- Deposit money into an account
- Withdraw money from an account
- View the total balance of all clients

The system also validates account balances during withdrawals to prevent withdrawing more than the available balance.

---

### User Management

The system includes a separate user management section for managing users who can access the application.

Available operations:

- Show all users
- Add new users
- Update users
- Delete users
- Find users
- Prevent duplicate usernames

Each user has:

- Username
- Password
- Permission level

The built-in `Admin` account is protected from deletion.

---

### Login System

Users must log in before accessing the main system.

The login process:

1. Requests a username.
2. Requests a password.
3. Checks the credentials against the stored users.
4. Grants access when the credentials are valid.
5. Repeats the login process when the credentials are incorrect.

---

### Permission System

The application includes a permission system that controls which parts of the application each user can access.

Permissions include:

| Permission | Operation |
|---|---|
| Show Clients | View all client accounts |
| Add Client | Add new clients |
| Delete Client | Delete client accounts |
| Update Client | Modify client information |
| Find Client | Search for clients |
| Transactions | Access banking transactions |
| Manage Users | Manage system users |

Permissions are represented using **bit flags**, allowing multiple permissions to be combined into a single integer.

Users can also be assigned **all permissions**.

When a user attempts to access an operation they are not authorized to use, the system displays an access-denied message.

---

## Data Persistence

The application uses **text files** to store its data instead of a database.

### Client Data

Client records are stored in:

```text
clientData.txt
```

Records use a custom delimiter:

```text
#//#
```

A client record follows this format:

```text
AccountNumber#//#PIN#//#Name#//#PhoneNumber#//#Balance
```

### User Data

User records are stored in:

```text
users.txt
```

The format is:

```text
Username#//#Password#//#Permission
```

When the program starts, the stored data is loaded into vectors. Changes are written back to the files when required.

---

## Project Structure

```text
Bank-Management-System/
│
├── Source.cpp
├── MyLib.h
├── Source.h
├── clientData.txt
├── users.txt
└── README.md
```

### `Source.cpp`

Contains the main application logic, including:

- Client management
- User management
- Authentication
- Permissions
- Transactions
- File handling
- Menus and navigation

### `MyLib.h`

Contains reusable helper functions for tasks such as:

- Reading numbers
- Reading strings
- Input validation
- Reading numbers within a range
- Generating random numbers
- Array utilities
- Splitting strings

### `clientData.txt`

Stores the persistent client records.

### `users.txt`

Stores the persistent user accounts and their permissions.

---

## Main Menu

After successfully logging in, users can access the main menu:

```text
=======================================
             Main Menu
=======================================
[1] Show all clients
[2] Add new client
[3] Delete client
[4] Update client
[5] Find client
[6] Transactions
[7] Manage users
[8] Logout
=======================================
```

The available operations depend on the permissions assigned to the logged-in user.

---

## How It Works

The general application flow is:

```text
Start Application
       │
       ▼
Load Users
       │
       ▼
     Login
       │
       ▼
Load Clients
       │
       ▼
   Main Menu
       │
       ├── Client Management
       │
       ├── Transactions
       │
       ├── User Management
       │
       └── Logout
```

When a user logs out, the application returns to the login process, allowing another stored user to sign in.

---

## Example Data

### Client

```text
HTY77869#//#1234#//#Mohamed gamal#//#01148386634#//#12000.000000
```

Represents:

```text
Account Number : HTY77869
PIN            : 1234
Name           : Mohamed gamal
Phone          : 01148386634
Balance        : 12000
```

### User

```text
Admin#//#1234#//#-1
```

The `-1` permission value represents all available permissions.

---

## Status

**Completed**

This project represents a functional console-based banking system and serves as a practical C++ project demonstrating how multiple programming concepts can be combined into a single application.
