# Wallet Balance – Manual Test Cases

Module: Wallet – Balance Management  
Test Type: Manual  
Priority: High  
Risk Level: Critical (Financial Accuracy)

---

## TS_WALLET_001 – View wallet balance after successful login

### TC_WALLET_001_01 – View wallet balance after successful login
  

### Preconditions
- User has a registered and active account
- User has a non-zero wallet balance
- Application is installed and accessible
- Internet connection is stable

### Test Steps
1. Launch the wallet application
2. Navigate to the login screen
3. Enter valid username/email
4. Enter valid password
5. Tap the **Login** button
6. Wait until the dashboard/home screen is fully loaded
7. Observe the wallet balance displayed on the dashboard

### Expected Result
- User is successfully logged in
- Wallet dashboard is displayed
- Wallet balance is visible without delay
- Displayed balance matches the user’s account balance
- No error or loading message is shown

### Priority
High

### Test Type
Functional


## TS_WALLET_002 – Balance matches backend data

### TC_WALLET_002_01 – Wallet balance matches backend API data

Precondition:
- User is logged in
- User has an active wallet with known balance
- Backend/API is accessible

Steps:
1. Login to the application
2. Navigate to Wallet / Dashboard page
3. Note the wallet balance displayed on UI
4. Fetch wallet balance from backend/API (via API tool / logs / mock data)
5. Compare UI balance with backend value

Expected Result:
- Wallet balance shown in UI matches backend/API balance exactly
- No discrepancy in amount or decimal precision

### TC_WALLET_002_02 – Wallet balance remains consistent after page refresh

Precondition:
- User is logged in
- Wallet balance is available

Steps:
1. Navigate to Wallet page
2. Note displayed wallet balance
3. Refresh the page
4. Observe wallet balance again

Expected Result:
- Wallet balance after refresh matches backend value
- No unexpected change in balance

### TC_WALLET_002_03 – Balance not loaded when backend API fails

Precondition:
- User is logged in
- Backend/API returns error (500 / 503)

Steps:
1. Login to the application
2. Navigate to Wallet page
3. Simulate backend/API failure
4. Observe wallet balance section

Expected Result:
- Wallet balance is NOT displayed as incorrect or stale data
- Appropriate error message is shown (e.g. "Unable to load balance")
- No misleading balance value is displayed

### TC_WALLET_002_04 – Balance not loaded during network timeout

Precondition:
- User is logged in
- Network is unstable or request times out

Steps:
1. Login to the application
2. Navigate to Wallet page
3. Simulate slow or disconnected network
4. Observe wallet balance behavior

Expected Result:
- Loading indicator is shown during timeout
- Error message is displayed if request fails
- Wallet balance is not shown incorrectly

### TC_WALLET_002_05 – Handle null or invalid balance response from backend

Precondition:
- User is logged in
- Backend/API returns null or malformed balance data

Steps:
1. Login to the application
2. Navigate to Wallet page
3. Simulate invalid backend response
4. Observe wallet balance section

Expected Result:
- Application handles error gracefully
- Wallet balance is not displayed incorrectly
- Appropriate fallback or error message is shown


## TS_WALLET_003 – Balance decreases after successful fund transfer

### TC_WALLET_003_01 – Sender balance decreases after successful transfer

Precondition:
- Sender is logged in
- Sender wallet has sufficient balance
- Receiver account is valid
- Balance calculation respects decimal precision (no rounding loss)


Steps:
1. Login as sender
2. Navigate to Wallet page
3. Note sender’s initial wallet balance
4. Initiate a fund transfer with a valid amount
5. Complete transfer successfully
6. Return to Wallet page
7. Observe sender’s wallet balance

Expected Result:
- Sender wallet balance is reduced
- Deducted amount equals transfer amount (plus fee if applicable)
- Balance calculation is correct

### TC_WALLET_003_02 – Sender balance matches backend after successful transfer

Precondition:
- Successful transfer has been completed

Steps:
1. Complete a fund transfer
2. Fetch updated balance from backend/API
3. Compare backend balance with UI balance

Expected Result:
- UI balance matches backend/API balance
- No discrepancy between frontend and backend

### TC_WALLET_003_03 – Balance remains unchanged after failed transfer

Precondition:
- Sender is logged in
- Sender has sufficient balance

Steps:
1. Note sender’s initial wallet balance
2. Initiate transfer with invalid recipient or forced failure
3. Transfer fails
4. Return to Wallet page

Expected Result:
- Wallet balance remains unchanged
- No partial deduction occurs
- User is informed transfer failed

### TC_WALLET_003_04 – Transfer blocked when balance is insufficient

Precondition:
- Sender balance is less than transfer amount

Steps:
1. Login as sender
2. Attempt to transfer amount greater than wallet balance
3. Submit transfer

Expected Result:
- Transfer is rejected
- Wallet balance remains unchanged
- Appropriate error message is shown

### TC_WALLET_003_05 – Transfer full wallet balance

Precondition:
- Sender wallet balance equals transfer amount (or minus fee)

Steps:
1. Login as sender
2. Transfer full available balance
3. Complete transfer
4. Check wallet balance

Expected Result:
- Wallet balance becomes zero (or minimum allowed)
- No negative balance occurs

### TC_WALLET_003_06 – Prevent duplicate balance deduction on double submission

Precondition:
- Sender has sufficient balance

Steps:
1. Initiate a transfer
2. Rapidly submit transfer twice (double click / retry)
3. Observe wallet balance

Expected Result:
- Balance is deducted only once
- No duplicate transaction occurs

manual-testing/test-cases/wallet-balance-test-cases.md

## TS_WALLET_004 – Balance increases after receiving funds

### TC_WALLET_004_01 – Receiver balance increases after receiving funds

Precondition:
- Sender and receiver accounts are valid
- Receiver is logged in or can log in after transfer
- Transfer is successful
- Balance calculation respects decimal precision (no rounding loss)


Steps:
1. Login as receiver
2. Navigate to Wallet page
3. Note receiver’s initial wallet balance
4. Sender completes a fund transfer to receiver
5. Refresh Wallet page (if needed)
6. Observe receiver’s wallet balance

Expected Result:
- Receiver wallet balance increases
- Increased amount equals received transfer amount

### TC_WALLET_004_02 – Receiver balance matches backend after receiving funds

Precondition:
- Transfer has been successfully completed

Steps:
1. Fetch updated receiver balance from backend/API
2. Compare backend balance with UI balance

Expected Result:
- Receiver UI balance matches backend/API data
- No mismatch in value or precision

### TC_WALLET_004_03 – Receiver balance remains unchanged after failed transfer

Precondition:
- Sender initiates transfer that fails

Steps:
1. Note receiver’s initial wallet balance
2. Sender attempts transfer that fails
3. Receiver checks wallet balance

Expected Result:
- Receiver balance remains unchanged
- No partial or incorrect credit occurs

### TC_WALLET_004_04 – Prevent duplicate balance increase for duplicate transfer

Precondition:
- Sender attempts duplicate submission

Steps:
1. Sender submits transfer multiple times rapidly
2. Receiver checks wallet balance

Expected Result:
- Receiver balance increases only once
- Only one transaction record exists

### TC_WALLET_004_05 – Receiver balance updates after login post-transfer

Precondition:
- Receiver is logged out during transfer

Steps:
1. Sender completes transfer
2. Receiver logs in
3. Navigate to Wallet page

Expected Result:
- Updated balance is shown correctly
- No stale data is displayed

### TC_WALLET_004_06 – Receiver balance update during delayed network response

Precondition:
- Network latency exists

Steps:
1. Sender completes transfer
2. Receiver opens Wallet page under slow network
3. Observe balance loading behavior

Expected Result:
- Loading indicator is shown
- Balance updates correctly once data is retrieved


## Automation Candidates – Wallet Balance Module

The following test cases are recommended for automation based on stability,
business criticality, and regression value.

### Recommended for Automation
- TC_WALLET_001_01 – View wallet balance after successful login
- TC_WALLET_002_01 – Wallet balance matches backend API data
- TC_WALLET_002_02 – Wallet balance remains consistent after page refresh
- TC_WALLET_003_01 – Sender balance decreases after successful transfer
- TC_WALLET_004_01 – Receiver balance increases after receiving funds

Reason:
- High business impact
- Frequently executed in regression testing
- Stable and predictable flows
- Suitable for UI + API assertion automation

### Keep Manual
- TC_WALLET_002_03 – Backend/API failure handling
- TC_WALLET_002_04 – Network timeout scenarios
- TC_WALLET_002_05 – Invalid or null backend response
- TC_WALLET_003_06 – Duplicate submission edge cases
- TC_WALLET_004_06 – Delayed network response handling

Reason:
- Hard to reliably simulate in automation
- Better validated through exploratory or controlled manual testing
- Environment-dependent behavior



