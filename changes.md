# Changes to trans.c - Bank Account Management System

## Overview
Complete implementation of a comprehensive Bank Account Management System with advanced features including account management, fund transfers, and statistical analysis.

## Core Features Implemented

### 1. **File Structure & Data Management**
- Implemented `clientData` structure with fields:
  - `acctNum`: Account number (1-100)
  - `lastName`: Last name (max 15 characters)
  - `firstName`: First name (max 10 characters)
  - `balance`: Account balance (double)
- Random-access file handling using credit.dat binary file

### 2. **Account Operations (CRUD)**

#### Create Account (`newRecord`)
- Add new account with account number, name, and initial balance
- Input validation for account number (1-100)
- Prevents duplicate account creation
- Safe string parsing with buffer overflow protection

#### Read Account (`viewAccount`)
- View specific account details without modification
- Displays account in formatted table
- Handles non-existent accounts gracefully

#### Update Account (`updateRecord`)
- Update account balance with charges or payments
- Validates account existence
- Transaction amount input with error handling
- Displays updated record after modification

#### Delete Account (`deleteRecord`)
- Remove account information by clearing the record
- Validates account existence before deletion
- Confirmation message upon successful deletion

### 3. **Advanced Features**

#### Export to Text File (`textFile`)
- Creates formatted accounts.txt file for printing
- Displays all active accounts in tabular format
- Includes headers: Acct, Last Name, First Name, Balance

#### Display All Accounts (`displayAllAccounts`)
- Shows all active accounts directly to console
- Formatted table output with proper alignment
- Reports if no active accounts exist

#### Fund Transfers (`transferFunds`)
- Transfer money between two accounts
- Validates both source and destination accounts
- Checks for sufficient funds before transfer
- Prevents self-transfer (same account)
- Updates both accounts atomically
- Displays transfer confirmation

#### Bank Statistics (`showStatistics`)
- Calculates total active accounts
- Computes total bank balance
- Identifies highest balance account
- Displays statistics in formatted box

### 4. **User Interface**

#### Main Menu (`enterChoice`)
- Clear menu display with all available options
- Numbered choices (1-9) for user selection
- Exit option (9) for program termination

#### Menu Options:
1. Store formatted text file for printing
2. Update an account
3. Add a new account
4. Delete an account
5. View a specific account
6. Display all active accounts
7. Transfer funds between accounts
8. Show bank statistics
9. End program

### 5. **Input Validation & Safety**

#### Helper Functions:
- `clearInputBuffer()`: Safely clears stdin buffer to prevent input overflow
- `getValidUnsignedInt()`: Validates unsigned integer input with error messages

#### Input Protection:
- Buffer overflow prevention with size limitations
- Validation of account numbers (1-100 range)
- Validation of transaction amounts (positive numbers)
- Safe string parsing with `sscanf()` and buffer limits

### 6. **Error Handling**
- File creation/opening validation
- Account existence checks
- Duplicate account prevention
- Insufficient funds detection
- Invalid input handling with user-friendly messages
- EOF and file operation error handling

## Key Enhancements

1. **Data Persistence**: All data saved to binary file for persistent storage
2. **Transaction Safety**: Atomic operations for fund transfers
3. **User Validation**: Comprehensive input validation for all operations
4. **Formatted Output**: Consistent table formatting for all displays
5. **Error Messages**: Clear, descriptive error messages for all failure cases
6. **Menu System**: Simple, intuitive menu-driven interface
7. **Account Limits**: Support for up to 100 accounts
8. **Statistics Tracking**: Real-time bank statistics calculation

## Program Flow

1. Program starts and opens/creates credit.dat file
2. Main menu is displayed to user
3. User selects an operation (1-8)
4. Selected operation is executed
5. File is updated if necessary
6. User is returned to menu (or program exits if option 9 is chosen)
7. File is properly closed on program exit

## File Operations

- **credit.dat**: Binary file for persistent account storage
- **accounts.txt**: Text file generated for printing/export

## Constants Defined

- `MAX_ACCOUNTS`: 100 (maximum account limit)
- `LAST_NAME_LEN`: 15 (last name buffer size)
- `FIRST_NAME_LEN`: 10 (first name buffer size)

## Technical Improvements

- Safe file seeking using `fseek()` and `SEEK_SET`/`SEEK_CUR`
- Proper file pointer management
- Use of `fread()` and `fwrite()` for binary file operations
- String boundary protection with `strncpy()`
- Safe input handling with `fgets()` and `sscanf()`
