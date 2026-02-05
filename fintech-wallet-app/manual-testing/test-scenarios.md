**Test Scenarios – Fund Transfer Feature**

Module: Wallet – Fund Transfer  
Test Type: Manual  
Priority: High  
Risk Level: Critical (Financial Transactions)


1. Authentication & Security Scenarios:
  - TS_AUTH_001 – User logs in with valid credentials:
    * Verify user can log in using registered email and correct password
    * Verify user is redirected to dashboard after successful login

  - TS_AUTH_002 – User logs in with invalid password
    * Verify error message is displayed
    * Verify user is not logged in
    * Verify error message does not expose sensitive information

  - TS_AUTH_003 – User account locked after multiple failed login attempts
    * Verify account is temporarily locked after defined number of failed attempts
    * Verify appropriate error message is shown

  - TS_AUTH_004 – Session timeout handling
    * Verify user session expires after inactivity
    * Verify user is redirected to login page after session timeout

2. Wallet Balance Management Scenarios
  - TS_WALLET_001 – View wallet balance
    * Verify user can view current wallet balance after login
    * Verify balance matches backend/API data

  - TS_WALLET_002 – Wallet balance update after successful transfer
    * Verify wallet balance decreases after sending funds
    * Verify wallet balance increases after receiving funds

  - TS_WALLET_003 – Wallet balance precision and rounding
    * Verify wallet supports decimal values correctly
    * Verify no rounding errors occur during calculations

3. Fund Transfer Scenarios (High Risk – Core Feature)
  - TS_TRANSFER_001 – User successfully transfers funds to another registered wallet user
    * Verify user can transfer funds to another registered user
    * Verify transaction is completed successfully
    * Verify sender and receiver balances update correctly

  - TS_TRANSFER_002 – Transfer amount exceeds wallet balance
    * Verify transfer is blocked
    * Verify appropriate error message is displayed
    * Verify wallet balance remains unchanged

  - TS_TRANSFER_003 – Transfer with zero or negative amount
    * Verify system prevents zero or negative transfers
    * Verify validation message is displayed
      
  - TS_TRANSFER_004 – Transfer to invalid or non-existent user
    * Verify transfer fails
    * Verify clear and user-friendly error message is shown
      
  - TS_TRANSFER_005 – Duplicate transfer submission
    * Verify system prevents duplicate transactions when user clicks submit multiple times
    * Verify only one transaction is recorded

4. Transaction History Scenarios
  - TS_HISTORY_001 – View transaction history list
    * Verify transaction history is displayed correctly
    * Verify transactions are sorted by date (latest first)

  - TS_HISTORY_002 – Transaction details accuracy
    * Verify transaction amount, date, and recipient/sender are correct
    * Verify transaction status is displayed correctly (success / failed)

  - TS_HISTORY_003 – No transaction history
    * Verify empty state message is shown when no transactions exist

5. Error Handling & Edge Case Scenarios
  - TS_ERROR_001 – Network interruption during transfer
    * Verify appropriate error message is displayed
    * Verify transaction is not partially processed

  - TS_ERROR_002 – Backend/API failure handling
    * Verify user receives friendly error message
    * Verify system does not crash or freeze

  -   - TS_ERROR_003 – Page refresh during transaction
    * Verify system handles refresh gracefully
    * Verify transaction consistency is maintained

6. Basic UX & Usability Scenarios
  - TS_UX_001 – Form validation messages
    * Verify validation messages are clear and easy to understand
    * Verify required fields are clearly marked

  - TS_UX_002 – Loading indicators
    * Verify loading indicator is shown during transfer processing
    * Verify user cannot submit form multiple times while loading

7. 7. Exploratory Testing Scenarios

  - TS_TRANSFER_EXP_001 – Exploratory testing for fund transfer edge cases

Description:
Explore unexpected user behavior during fund transfer, such as rapid input changes,
session timeout, app backgrounding, or unusual numeric formats.

Goal:
Identify edge cases not covered by predefined scenarios.


## Scenario to Test Case Mapping

Each test scenario in this document is converted into one or more detailed manual test cases located at:

manual-testing/test-cases/transfer-test-cases.md

