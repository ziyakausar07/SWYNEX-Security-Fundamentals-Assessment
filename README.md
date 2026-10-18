# SWYNEX Security Fundamentals Assessment

## Internship Details
- **Organization:** SWYNEX Technologies
- **Task:** Task 1 – Security Fundamentals Assessment
- **Project:** Orphanage Management System
- **Domain:** Cyber Security

## 1. Objective
The objective of this assessment is to identify an API access control risk, implement a security improvement, and verify the result.

## 2. Scope
- **Frontend:** https://orphanage-management-system-iota.vercel.app/
- **Backend:** https://orphanagemanagementsystem.onrender.com/
- **Tested API:** `GET /api/admin/dashboard`

## 3. Security Finding
### Missing Authentication on Admin Dashboard API

**Affected Component:** `/api/admin/dashboard`

**Initial Observation:** Before the security fix, opening the dashboard API endpoint without logging in returned dashboard statistics.

**Risk:** Unauthenticated users could potentially access administrative dashboard information.

## 4. Mitigation Implemented
The dashboard route was updated to use the existing `@role_required("ADMIN")` decorator to require an admin role before returning the dashboard response.

## 5. Retesting Results
- **Without authentication:** The API returned an authorization-required message.
- **Admin login:** The dashboard continued to load successfully after logging in as an administrator.

These results indicate that the tested endpoint now requires authentication. The exact HTTP status code was not recorded.

## 6. Evidence
The following screenshots will be added to the `evidence` folder:
1. `01_Admin_Dashboard_Login.png`
2. `02_Before_Security_Fix.png`
3. `03_After_Security_Fix.png`
4. `04_Dashboard_After_Fix.png`

## 7. Recommendations
- Review other admin-only API routes for authentication and authorization.
- Keep passwords, JWT tokens, and secret keys out of public repositories.
- Review security headers and apply appropriate protections.
- Retest protected endpoints after security changes.

## 8. Conclusion
This assessment identified a potential missing-authentication issue in the admin dashboard API. An admin-role check was added, and retesting showed an authorization-required response when authentication was missing. The authenticated admin dashboard continued to work successfully.

**Scope Note:** The findings and retesting described here apply to the endpoint tested. Other API routes require separate assessment.
