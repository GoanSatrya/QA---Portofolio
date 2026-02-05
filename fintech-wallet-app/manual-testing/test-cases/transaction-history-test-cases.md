# Transaction History – Manual Test Cases

Module: Wallet – Transaction History  
Test Type: Manual  
Priority: High  
Risk Level: High (Financial Records & Auditability)


## TS_HISTORY_001 – View transaction history list

### TC_HISTORY_001_01 – View transaction history after successful login
Precondition:
- User is logged in
- User has at least one completed transaction

Steps:
1. Login to the application
2. Navigate to Transaction History page
3. Observe the transaction list

Expected Result:
- Transaction history list is displayed
- Transactions are visible without error
- Each transaction shows basic details (amount, date, status)

### TC_HISTORY_001_02 – Transaction list sorted by latest first
Precondition:
- User has multiple transactions on different dates

Steps:
1. Navigate to Transaction History page
2. Observe the order of transactions

Expected Result:
- Transactions are sorted by date
- Most recent transaction appears at the top


## TS_HISTORY_002 – Transaction details accuracy

### TC_HISTORY_002_01 – Transaction details match backend data
Precondition:
- User has completed at least one transfer

Steps:
1. Navigate to Transaction History
2. Select a transaction
3. Note transaction amount, date, and status
4. Fetch transaction data from backend/API
5. Compare UI data with backend data

Expected Result:
- UI transaction details match backend/API data
- No mismatch in amount, date, or status

### TC_HISTORY_002_02 – Correct sender and receiver displayed
Precondition:
- Transaction between two users exists

Steps:
1. Open transaction history
2. Select a transaction
3. Observe sender and receiver information

Expected Result:
- Sender and receiver are displayed correctly
- No incorrect user mapping


## TS_HISTORY_003 – No transaction history (empty state)

### TC_HISTORY_003_01 – Empty transaction history state
Precondition:
- User has no transaction history

Steps:
1. Login to the application
2. Navigate to Transaction History page

Expected Result:
- Empty state message is displayed
- Message clearly indicates no transactions found
- No error or broken UI is shown


## TS_HISTORY_004 – Failed and pending transactions

### TC_HISTORY_004_01 – Failed transaction is displayed correctly
Precondition:
- User has at least one failed transaction

Steps:
1. Navigate to Transaction History
2. Locate failed transaction

Expected Result:
- Transaction status is marked as “Failed”
- Amount is not deducted or credited incorrectly

### TC_HISTORY_004_02 – Pending transaction status handling
Precondition:
- Transaction is in pending state

Steps:
1. Navigate to Transaction History
2. Observe pending transaction

Expected Result:
- Transaction status is shown as “Pending”
- UI updates once transaction is completed or failed


## TS_HISTORY_005 – Error & edge cases

### TC_HISTORY_005_01 – History not loaded due to backend failure
Precondition:
- Backend/API is unavailable

Steps:
1. Navigate to Transaction History page
2. Simulate backend/API failure

Expected Result:
- User-friendly error message is displayed
- Transaction history is not shown incorrectly

### TC_HISTORY_005_02 – Network interruption while loading history
Precondition:
- Network connection is unstable

Steps:
1. Navigate to Transaction History
2. Simulate network interruption

Expected Result:
- Loading indicator or error message is shown
- Application does not freeze or crash


## Automation Candidates – Transaction History Module

### Recommended for Automation
- TC_HISTORY_001_01 – View transaction history after login
- TC_HISTORY_001_02 – Transaction list sorted by latest first
- TC_HISTORY_002_01 – Transaction details match backend
- TC_HISTORY_004_01 – Failed transaction display

Reason:
- Stable UI flows
- High regression value
- Easy backend validation

### Keep Manual
- Network interruption scenarios
- Backend failure handling
- Pending transaction state timing

Reason:
- Environment dependent
- Hard to reliably automate




