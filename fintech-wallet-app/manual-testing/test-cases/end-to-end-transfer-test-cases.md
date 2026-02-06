# End-to-End – Fund Transfer Flow Test Cases

Module: Wallet – End-to-End Flow  
Test Type: Manual  
Priority: Critical  
Risk Level: Critical (Financial Transaction Integrity)

## E2E Happy Path (MOST IMPORTANT)
### TC_E2E_001 – Successful fund transfer reflected in balance and transaction history
Precondition:
- Sender and receiver accounts exist
- Sender has sufficient wallet balance
- Both accounts are active

Steps:
1. Login as Sender
2. Navigate to Wallet page
3. Note sender’s initial wallet balance
4. Initiate fund transfer to valid receiver
5. Enter valid transfer amount
6. Submit transfer
7. Verify transfer success confirmation
8. Navigate back to Wallet page
9. Verify sender’s wallet balance is reduced correctly
10. Navigate to Transaction History
11. Verify transaction is listed with correct details
12. Logout sender
13. Login as Receiver
14. Navigate to Wallet page
15. Verify receiver’s wallet balance is increased correctly
16. Navigate to Transaction History
17. Verify incoming transaction is listed correctly

Expected Result:
- Transfer completes successfully
- Sender balance is deducted correctly
- Receiver balance is credited correctly
- Transaction appears correctly in both users’ history
- Transaction details match backend data

## E2E Negative Flow – Failed transfer
### TC_E2E_001 – Successful fund transfer reflected in balance and transaction history
Precondition:
- Sender and receiver accounts exist
- Sender has sufficient wallet balance
- Both accounts are active

Steps:
1. Login as Sender
2. Navigate to Wallet page
3. Note sender’s initial wallet balance
4. Initiate fund transfer to valid receiver
5. Enter valid transfer amount
6. Submit transfer
7. Verify transfer success confirmation
8. Navigate back to Wallet page
9. Verify sender’s wallet balance is reduced correctly
10. Navigate to Transaction History
11. Verify transaction is listed with correct details
12. Logout sender
13. Login as Receiver
14. Navigate to Wallet page
15. Verify receiver’s wallet balance is increased correctly
16. Navigate to Transaction History
17. Verify incoming transaction is listed correctly

Expected Result:
- Transfer completes successfully
- Sender balance is deducted correctly
- Receiver balance is credited correctly
- Transaction appears correctly in both users’ history
- Transaction details match backend data

## E2E Negative Flow – Failed transfer
### TC_E2E_002 – Failed transfer does not affect balances or history
Precondition:
- Sender account exists
- Sender has sufficient balance
- Invalid receiver or forced failure condition

Steps:
1. Login as Sender
2. Note sender’s wallet balance
3. Attempt fund transfer with invalid recipient
4. Submit transfer
5. Verify transfer fails
6. Navigate to Wallet page
7. Check sender wallet balance
8. Navigate to Transaction History

Expected Result:
- Transfer fails with clear error message
- Sender wallet balance remains unchanged
- No successful transaction record is created

## E2E Edge Case – Duplicate submission
### TC_E2E_003 – Duplicate submission does not create duplicate transactions
Precondition:
- Sender has sufficient balance

Steps:
1. Login as Sender
2. Initiate fund transfer
3. Rapidly click submit multiple times
4. Observe system behavior
5. Navigate to Wallet page
6. Navigate to Transaction History

Expected Result:
- Only one transfer is processed
- Wallet balance is deducted once
- Only one transaction record exists

## E2E Session Handling
### TC_E2E_004 – Session timeout during fund transfer
Precondition:
- Sender is logged in
- Session timeout threshold is configured

Steps:
1. Login as Sender
2. Navigate to Transfer page
3. Stay inactive until session expires
4. Attempt to submit transfer

Expected Result:
- User is redirected to login
- Transfer is not processed
- Wallet balance remains unchanged

## E2E Network Failure
### TC_E2E_005 – Network interruption during fund transfer
Precondition:
- Sender is logged in
- Network instability exists

Steps:
1. Initiate fund transfer
2. Disconnect network during submission
3. Restore network
4. Navigate to Wallet page
5. Navigate to Transaction History

Expected Result:
- User receives appropriate error message
- No partial or duplicate transaction occurs
- Wallet balance remains consistent


## Automation Candidates – End-to-End Flow

### Recommended for Automation
- TC_E2E_001 – Successful fund transfer E2E
- TC_E2E_003 – Duplicate submission prevention

Reason:
- High business impact
- Ideal for regression automation
- Covers multiple modules in one flow

### Keep Manual
- Network interruption scenarios
- Session timeout handling

Reason:
- Environment and timing dependent
- Difficult to stabilize in automation










