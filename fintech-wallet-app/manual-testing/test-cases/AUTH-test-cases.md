# Manual Test Cases – Authentication Feature

Module: Authentication (Login / Logout)  
Priority: High  
Risk Level: Critical (Account Access & Security)


**TC_AUTH_001 – Successful login with valid credentials**

| Field          | Description |
|---------------|-------------|
| Test Case ID  | TC_AUTH_001 |
| Scenario ID   | TS_AUTH_001 |
| Title         | Successful login with valid email and password |
| Preconditions| User is registered and active |
| Test Data     | Email: valid_user@email.com, Password: valid_password |
| Steps         | 1. Navigate to Login page<br>2. Enter valid email<br>3. Enter valid password<br>4. Click Login |
| Expected Result | User is logged in successfully and redirected to dashboard |
| Post-condition | User session is created |

**TC_AUTH_002 – Login with invalid password**

| Field          | Description |
|---------------|-------------|
| Test Case ID  | TC_AUTH_002 |
| Scenario ID   | TS_AUTH_002 |
| Title         | Login fails with incorrect password |
| Preconditions| User is registered and active |
| Test Data     | Email: valid_user@email.com, Password: wrong_password |
| Steps         | 1. Navigate to Login page<br>2. Enter valid email<br>3. Enter invalid password<br>4. Click Login |
| Expected Result | Generic error message displayed without revealing which credential is incorrect |
| Post-condition | User is not logged in |

**TC_AUTH_003 – Login with unregistered email**

| Field          | Description |
|---------------|-------------|
| Test Case ID  | TC_AUTH_003 |
| Scenario ID   | TS_AUTH_003 |
| Title         | Login fails with non-existent email |
| Preconditions| User does not exist in system |
| Test Data     | Email: unknown@email.com, Password: any_password |
| Steps         | 1. Navigate to Login page<br>2. Enter unregistered email<br>3. Enter password<br>4. Click Login |
| Expected Result | Generic error message displayed without revealing which credential is incorrect |
| Post-condition | No session created |

**TC_AUTH_004 – Login with empty credentials**

| Field          | Description |
|---------------|-------------|
| Test Case ID  | TC_AUTH_004 |
| Scenario ID   | TS_AUTH_004 |
| Title         | Prevent login with empty email and password |
| Preconditions| User is on login page |
| Test Data     | Email: empty, Password: empty |
| Steps         | 1. Navigate to Login page<br>2. Leave email field empty<br>3. Leave password field empty<br>4. Click Login |
| Expected Result | Validation messages displayed for required fields |
| Post-condition | User remains on login page |

**TC_AUTH_005 – Successful logout**

| Field | Description |
|------|------------|
| Test Case ID | TC_AUTH_005 |
| Scenario ID | TS_AUTH_005 |
| Title | User logs out successfully |
| Preconditions | User is logged in |
| Test Data | N/A |
| Steps | 1. User is logged in<br>2. Click Logout button |
| Expected Result | User is logged out and redirected to login page |
| Post-condition | User session is terminated |

**TC_AUTH_006 – Access protected page after logout**

| Field | Description |
|------|------------|
| Test Case ID | TC_AUTH_006 |
| Scenario ID | TS_AUTH_006 |
| Title | Prevent access to protected pages after logout |
| Preconditions | User was logged in and has logged out |
| Test Data | Protected URL (e.g. /dashboard) |
| Steps | 1. Logout from application<br>2. Attempt to access protected page via URL |
| Expected Result | User is redirected to login page |
| Post-condition | No active session |

**TC_AUTH_007 – Session timeout due to inactivity**

| Field | Description |
|------|------------|
| Test Case ID | TC_AUTH_007 |
| Scenario ID | TS_AUTH_007 |
| Title | Session expires after inactivity |
| Preconditions | User is logged in |
| Test Data | Inactivity duration exceeds timeout limit |
| Steps | 1. Login successfully<br>2. Remain inactive until session timeout<br>3. Perform any action |
| Expected Result | User is logged out and prompted to login again |
| Post-condition | Session expired |

**TC_AUTH_008 – Multiple failed login attempts**

| Field | Description |
|------|------------|
| Test Case ID | TC_AUTH_008 |
| Scenario ID | TS_AUTH_008 |
| Title | Account protection after multiple failed login attempts |
| Preconditions | User account exists and is active |
| Test Data | Valid email, incorrect password repeated multiple times |
| Steps | 1. Navigate to login page<br>2. Enter valid email and wrong password multiple times |
| Expected Result | Account is temporarily locked or CAPTCHA is triggered |
| Post-condition | Account protected against brute-force attack |


## Automation Candidates
- TC_AUTH_001 (Login happy path)
- TC_AUTH_002 (Invalid password)
- TC_AUTH_004 (Field validation)
- TC_AUTH_006 (Access after logout)







