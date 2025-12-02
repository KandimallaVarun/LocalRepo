#This is user-define dreadme file
# Manual Test Cases - User Authentication Module
**Version**: v2.1.0  
**Deployment Date**: 2025-12-02  
**Tester**: [Your Name]  
**Environment**: Staging (https://staging.app.com)  

## Test Case Summary
| ID | Test Case | Status | Priority | Severity |
|----|-----------|--------|----------|----------|
| TC_AUTH_001 | Login with valid credentials | PASS | High | High |
| TC_AUTH_002 | Login with invalid password | PASS | High | High |
| TC_AUTH_003 | Password reset flow | FAIL | Medium | Medium |
| TC_AUTH_004 | Session timeout | PASS | Low | Low |
| **Total: 4** | **3 PASS, 1 FAIL** | **75%** | | |

## Detailed Test Cases

### TC_AUTH_001: Login with valid credentials
**Preconditions**: User account exists with verified email  
**Test Steps**:
1. Navigate to `/login` page
2. Enter valid email: `testuser@company.com`
3. Enter valid password: `TestPass123!`
4. Click "Sign In" button
5. Verify dashboard loads

**Expected Result**: User redirected to dashboard, welcome message shows "Hello, Test User!"  
**Actual Result**: Dashboard loaded successfully with correct user greeting  
**Status**: ✅ PASS  
**Execution Time**: 45s  
**Remarks**: All good

### TC_AUTH_002: Login with invalid password
**Preconditions**: User account exists  
**Test Steps**:
1. Navigate to `/login` page
2. Enter valid email: `testuser@company.com`
3. Enter invalid password: `wrongpass`
4. Click "Sign In" button

**Expected Result**: Error message "Invalid credentials. Please try again." appears, user remains on login page  
**Actual Result**: Correct error message displayed in red banner  
**Status**: ✅ PASS  
**Execution Time**: 20s  
**Remarks**: Error styling consistent

### TC_AUTH_003: Password reset flow
**Preconditions**: User account exists  
**Test Steps**:
1. Navigate to `/login` page
2. Click "Forgot Password?" link
3. Enter email: `testuser@company.com`
4. Click "Reset Password"
5. Check inbox for reset email
6. Click reset link and set new password
7. Login with new password

**Expected Result**: Reset email delivered within 60s, new password accepted, login successful  
**Actual Result**: Reset email not received after 5 minutes  
**Status**: ❌ FAIL  
**Execution Time**: 5m 30s  
**Remarks**: Email service issue - raised bug #AUTH-45

### TC_AUTH_004: Session timeout
**Preconditions**: User logged in successfully  
**Test Steps**:
1. Login with valid credentials
2. Leave browser idle for 30 minutes
3. Try to access `/dashboard` page
4. Attempt to perform any action

**Expected Result**: Session expires, user redirected to login page with message "Your session has expired. Please login again."  
**Actual Result**: Correctly redirected to login with timeout message  
**Status**: ✅ PASS  
**Execution Time**: 32m  
**Remarks**: Timeout working as expected

---

**Overall Test Execution Notes**:  
- Critical login flows working except password reset  
- Related bugs: [#AUTH-45](https://github.com/team/project/issues/45)  
- Ready for production after email service fix
