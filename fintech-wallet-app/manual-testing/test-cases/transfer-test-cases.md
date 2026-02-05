Manual Test Cases – Fund Transfer Feature
Module: Wallet Fund Transfer
Priority: High
Risk Level: Critical (Financial Transaction)

**TC_TRANSFER_001 – Successful fund transfer to another valid user:**
| Field           | Description                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| Test Case ID    | TC_TRANSFER_001                                                                                         |
| Scenario ID     | TS_TRANSFER_001                                                                                         |
| Title           | Successful transfer to another registered user                                                          |
| Preconditions   | User A is logged in and has sufficient wallet balance                                                   |
| Test Data       | Recipient: User B, Amount: 100                                                                          |
| Steps           | 1. Navigate to Transfer page<br>2. Enter valid recipient<br>3. Enter transfer amount<br>4. Click Submit |
| Expected Result | Transfer is successful and confirmation message is displayed                                            |
| Post-condition  | Sender balance decreases, receiver balance increases                                                    |


**TC_TRANSFER_002 – Transfer amount exceeds wallet balance:**
| Field           | Description                                                                                                         |
| --------------- | ------------------------------------------------------------------------------------------------------------------- |
| Test Case ID    | TC_TRANSFER_002                                                                                                     |
| Scenario ID     | TS_TRANSFER_002                                                                                                     |
| Title           | Transfer blocked when amount exceeds balance                                                                        |
| Preconditions   | User is logged in with balance less than transfer amount                                                            |
| Test Data       | Amount > available balance                                                                                          |
| Steps           | 1. Navigate to Transfer page<br>2. Enter valid recipient<br>3. Enter amount greater than balance<br>4. Click Submit |
| Expected Result | Transfer is blocked with clear error message                                                                        |
| Post-condition  | Wallet balance remains unchanged                                                                                    |


**TC_TRANSFER_003 – Transfer with zero amount:**
| Field           | Description                                                                                         |
| --------------- | --------------------------------------------------------------------------------------------------- |
| Test Case ID    | TC_TRANSFER_003                                                                                     |
| Scenario ID     | TS_TRANSFER_003                                                                                     |
| Title           | Prevent transfer with zero amount                                                                   |
| Preconditions   | User is logged in                                                                                   |
| Test Data       | Amount: 0                                                                                           |
| Steps           | 1. Navigate to Transfer page<br>2. Enter valid recipient<br>3. Enter amount as 0<br>4. Click Submit |
| Expected Result | Validation message displayed, transfer not processed                                                |
| Post-condition  | No transaction created                                                                              |


**TC_TRANSFER_004 – Transfer with negative amount:**
| Field           | Description                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------- |
| Test Case ID    | TC_TRANSFER_004                                                                                         |
| Scenario ID     | TS_TRANSFER_003                                                                                         |
| Title           | Prevent transfer with negative amount                                                                   |
| Preconditions   | User is logged in                                                                                       |
| Test Data       | Amount: -50                                                                                             |
| Steps           | 1. Navigate to Transfer page<br>2. Enter valid recipient<br>3. Enter negative amount<br>4. Click Submit |
| Expected Result | Validation error shown, transfer blocked                                                                |
| Post-condition  | No transaction created                                                                                  |


**TC_TRANSFER_005 – Transfer to invalid or non-existent user:**
| Field           | Description                                                                                            |
| --------------- | ------------------------------------------------------------------------------------------------------ |
| Test Case ID    | TC_TRANSFER_005                                                                                        |
| Scenario ID     | TS_TRANSFER_004                                                                                        |
| Title           | Transfer fails when recipient does not exist                                                           |
| Preconditions   | User is logged in                                                                                      |
| Test Data       | Recipient: invalid user ID                                                                             |
| Steps           | 1. Navigate to Transfer page<br>2. Enter invalid recipient<br>3. Enter valid amount<br>4. Click Submit |
| Expected Result | Error message displayed indicating invalid recipient                                                   |
| Post-condition  | No balance change                                                                                      |


**TC_TRANSFER_006 – Duplicate transfer submission:**
| Field           | Description                                                     |
| --------------- | --------------------------------------------------------------- |
| Test Case ID    | TC_TRANSFER_006                                                 |
| Scenario ID     | TS_TRANSFER_005                                                 |
| Title           | Prevent duplicate transfer on multiple submit clicks            |
| Preconditions   | User is logged in with sufficient balance                       |
| Test Data       | Amount: 100                                                     |
| Steps           | 1. Fill transfer form<br>2. Click Submit multiple times rapidly |
| Expected Result | Only one transaction is processed                               |
| Post-condition  | Single transaction record exists                                |


**TC_TRANSFER_007 – Network interruption during transfer:**
| Field           | Description                                                     |
| --------------- | --------------------------------------------------------------- |
| Test Case ID    | TC_TRANSFER_007                                                 |
| Scenario ID     | TS_ERROR_001                                                    |
| Title           | Handle network interruption during transfer                     |
| Preconditions   | User is logged in                                               |
| Test Data       | Valid recipient and amount                                      |
| Steps           | 1. Start transfer<br>2. Simulate network loss during submission |
| Expected Result | User receives error message, no partial transaction             |
| Post-condition  | Balance remains consistent                                      |


Automation Candidates:
- TC_TRANSFER_001 (Happy path)
- TC_TRANSFER_006 (Duplicate submission prevention)

Remain Manual:
- Error handling
- Network failure scenarios
- Validation edge cases
