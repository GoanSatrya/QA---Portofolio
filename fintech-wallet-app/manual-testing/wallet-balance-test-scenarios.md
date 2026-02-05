# Test Scenarios – Wallet Balance Feature

Module: Wallet – Balance Management  
Test Type: Manual  
Priority: High  
Risk Level: Critical (Financial Accuracy)

## 1. Balance Display Scenarios

### TS_WALLET_001 – View wallet balance after login
- Verify user can view wallet balance after successful login
- Verify balance is displayed clearly on dashboard

### TS_WALLET_002 – Balance matches backend data
- Verify displayed wallet balance matches backend / API data
- Verify no discrepancy between UI and backend balance values

## 2. Balance Update Scenarios

### TS_WALLET_003 – Balance decreases after successful fund transfer
- Verify sender wallet balance decreases after transfer
- Verify deduction amount is correct

### TS_WALLET_004 – Balance increases after receiving funds
- Verify receiver wallet balance increases after receiving funds
- Verify credited amount is correct

### TS_WALLET_005 – Balance remains unchanged after failed transfer
- Verify wallet balance does not change when transfer fails
- Verify no partial deduction occurs

## 3. Precision & Formatting Scenarios

### TS_WALLET_006 – Decimal precision handling
- Verify wallet supports decimal values correctly
- Verify balance precision follows business rules (e.g. 2 decimal places)

### TS_WALLET_007 – Large balance values
- Verify system correctly displays large wallet balances
- Verify no UI truncation or overflow

## 4. Edge Case & Error Scenarios

### TS_WALLET_008 – Balance during concurrent transactions
- Verify balance remains consistent during multiple transactions
- Verify no race condition impacts balance accuracy

### TS_WALLET_009 – Balance display during network issues
- Verify appropriate message is shown if balance cannot be loaded
- Verify stale or incorrect balance is not displayed

## Scenario to Test Case Mapping

Each wallet balance test scenario in this document is converted into detailed manual test cases located at:

manual-testing/test-cases/wallet-balance-test-cases.md
