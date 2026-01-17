# Manual Testing Portfolio - Login Functionality

## Project Overview

**Application:** Demo Web Application
**Feature Under Test:** User Login Functionality
**Testing Type:** Black-box Testing (Manual)
**Tester:** Andreas Lang

---

## Test Scenarios

| ID | Scenario | Priority |
|----|----------|----------|
| TS-01 | Verify successful login with valid credentials | High |
| TS-02 | Verify login fails with invalid credentials | High |
| TS-03 | Verify login form validation | Medium |
| TS-04 | Verify password security features | High |
| TS-05 | Verify "Remember Me" functionality | Low |
| TS-06 | Verify "Forgot Password" link | Medium |

---

## Test Cases

### TC-001: Successful Login with Valid Credentials

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-001 |
| **Test Scenario** | TS-01 |
| **Priority** | High |
| **Preconditions** | User account exists in the system |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Enter valid username | testuser@email.com | Username field accepts input |
| 3 | Enter valid password | ValidPass123! | Password field shows masked characters |
| 4 | Click "Login" button | - | User is redirected to dashboard |

**Expected Result:** User successfully logs in and sees the dashboard with welcome message.

---

### TC-002: Login Fails with Invalid Password

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-002 |
| **Test Scenario** | TS-02 |
| **Priority** | High |
| **Preconditions** | User account exists in the system |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Enter valid username | testuser@email.com | Username field accepts input |
| 3 | Enter invalid password | WrongPassword | Password field shows masked characters |
| 4 | Click "Login" button | - | Error message is displayed |

**Expected Result:** Login fails. Error message "Invalid username or password" is displayed. User remains on login page.

---

### TC-003: Login Fails with Non-existent User

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-003 |
| **Test Scenario** | TS-02 |
| **Priority** | High |
| **Preconditions** | None |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Enter non-existent username | nobody@email.com | Username field accepts input |
| 3 | Enter any password | AnyPassword123 | Password field shows masked characters |
| 4 | Click "Login" button | - | Error message is displayed |

**Expected Result:** Login fails. Same generic error message "Invalid username or password" is displayed (security: don't reveal if user exists).

---

### TC-004: Empty Username Field Validation

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-004 |
| **Test Scenario** | TS-03 |
| **Priority** | Medium |
| **Preconditions** | None |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Leave username field empty | - | Field is empty |
| 3 | Enter valid password | ValidPass123! | Password field shows masked characters |
| 4 | Click "Login" button | - | Validation error is displayed |

**Expected Result:** Form validation prevents submission. Error message "Username is required" is displayed near the username field.

---

### TC-005: Empty Password Field Validation

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-005 |
| **Test Scenario** | TS-03 |
| **Priority** | Medium |
| **Preconditions** | None |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Enter valid username | testuser@email.com | Username field accepts input |
| 3 | Leave password field empty | - | Field is empty |
| 4 | Click "Login" button | - | Validation error is displayed |

**Expected Result:** Form validation prevents submission. Error message "Password is required" is displayed near the password field.

---

### TC-006: Password Field Masking

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-006 |
| **Test Scenario** | TS-04 |
| **Priority** | High |
| **Preconditions** | None |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Click on password field | - | Field is focused |
| 3 | Type password | SecretPassword | Characters are masked (shown as dots/asterisks) |

**Expected Result:** Password characters are hidden and displayed as masked characters for security.

---

### TC-007: SQL Injection Attempt

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-007 |
| **Test Scenario** | TS-04 |
| **Priority** | High |
| **Preconditions** | None |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Enter SQL injection in username | ' OR '1'='1 | Field accepts input |
| 3 | Enter any password | anything | Password field accepts input |
| 4 | Click "Login" button | - | Login fails safely |

**Expected Result:** Application handles input safely. No SQL error is exposed. Standard "Invalid username or password" message is shown.

---

### TC-008: Boundary Value - Minimum Password Length

| Field | Description |
|-------|-------------|
| **Test Case ID** | TC-008 |
| **Test Scenario** | TS-03 |
| **Priority** | Medium |
| **Preconditions** | Minimum password length is 8 characters |

**Test Steps:**

| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page is displayed |
| 2 | Enter valid username | testuser@email.com | Username field accepts input |
| 3 | Enter 7-character password | Pass123 | Password field accepts input |
| 4 | Click "Login" button | - | Validation or login error |

**Expected Result:** If validation exists, error "Password must be at least 8 characters" is shown. Otherwise, login fails with invalid credentials message.

---

## Testing Techniques Used

### Equivalence Partitioning

| Partition | Valid/Invalid | Example |
|-----------|---------------|---------|
| Valid username + valid password | Valid | testuser@email.com / ValidPass123! |
| Valid username + invalid password | Invalid | testuser@email.com / WrongPass |
| Invalid username + valid password | Invalid | nobody@email.com / ValidPass123! |
| Invalid username + invalid password | Invalid | nobody@email.com / WrongPass |
| Empty username | Invalid | (empty) |
| Empty password | Invalid | (empty) |

### Boundary Value Analysis

| Boundary | Test Values | Expected |
|----------|-------------|----------|
| Password min length (8) | 7 chars, 8 chars, 9 chars | 7: fail, 8: pass, 9: pass |
| Username max length (50) | 49 chars, 50 chars, 51 chars | 49: pass, 50: pass, 51: fail |

---

## Bug Report Example

### BUG-001: Error Message Reveals User Existence

| Field | Description |
|-------|-------------|
| **Bug ID** | BUG-001 |
| **Title** | Error message reveals whether username exists in system |
| **Severity** | Medium |
| **Priority** | High |
| **Environment** | Chrome 120, Windows 11 |
| **Build** | v1.2.3 |

**Description:**
When attempting to log in with a non-existent username, the error message "User not found" is displayed. This reveals to potential attackers which usernames exist in the system.

**Steps to Reproduce:**
1. Navigate to /login
2. Enter username: nonexistent@test.com
3. Enter password: AnyPassword123
4. Click "Login" button

**Actual Result:**
Error message: "User not found"

**Expected Result:**
Generic error message: "Invalid username or password" (same message for all login failures)

**Security Impact:**
Attackers can enumerate valid usernames by observing different error messages.

**Suggested Fix:**
Use the same generic error message for all authentication failures.

---

## Test Execution Summary

| Status | Count |
|--------|-------|
| Total Test Cases | 8 |
| Passed | 7 |
| Failed | 1 |
| Blocked | 0 |

**Pass Rate:** 87.5%

**Notes:**
- BUG-001 identified during TC-003 execution
- All security-related test cases passed except username enumeration issue
- Form validation working correctly

---

## Tools Used

- **Test Management:** Manual documentation (Markdown)
- **Browser:** Chrome DevTools for network inspection
- **Bug Tracking:** Jira (example format used)

---

*Document created by Andreas Lang - QA Portfolio*
