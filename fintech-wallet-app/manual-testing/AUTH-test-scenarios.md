## Test Scenarios – Authentication Feature

Module: Authentication (Login, Session, Logout)  
Test Type: Manual  
Priority: High  
Risk Level: Critical (Account Access & Security)


## 1. Login Scenarios

### TS_AUTH_001 – Successful login with valid credentials
- Verify user can log in with valid email and password
- Verify user is redirected to dashboard after login
- Verify authenticated session is created

### TS_AUTH_002 – Login with invalid password
- Verify login fails with incorrect password
- Verify error message is displayed
- Verify error message does not expose sensitive information
- Verify user remains on login page

### TS_AUTH_003 – Login with unregistered email
- Verify login fails for non-existent email
- Verify generic error message is shown
- Verify system does not reveal account existence

### TS_AUTH_004 – Login with empty credentials
- Verify login is blocked when email and password are empty
- Verify validation messages are displayed for required fields


## 2. Session Management Scenarios

### TS_AUTH_005 – Session persistence after login
- Verify user remains logged in after page refresh
- Verify session remains active within valid time window

### TS_AUTH_006 – Session timeout due to inactivity
- Verify user session expires after configured inactivity period
- Verify user is redirected to login page after timeout

### TS_AUTH_007 – Access protected page after session expiry
- Verify user cannot access dashboard after session expires
- Verify user is redirected to login page


## 3. Logout Scenarios

### TS_AUTH_008 – Successful logout
- Verify user can log out successfully
- Verify user session is terminated
- Verify user is redirected to login page

### TS_AUTH_009 – Access protected pages after logout
- Verify user cannot access protected pages after logout
- Verify user is redirected to login page when accessing restricted URLs


## 4. Security & Abuse Prevention Scenarios

### TS_AUTH_010 – Multiple failed login attempts
- Verify account is temporarily locked after defined number of failed attempts
- Verify appropriate error message is displayed

### TS_AUTH_011 – Error message consistency
- Verify error messages are consistent across login failures
- Verify messages do not expose system or account details

### TS_AUTH_012 – Concurrent session handling (optional)
- Verify user behavior when logged in on multiple devices/browsers
- Verify old session handling (remain active / invalidated based on policy)



## Scenario to Test Case Mapping

Each authentication test scenario in this document is covered by detailed manual test cases located at:

manual-testing/test-cases/AUTH-test-cases.md





