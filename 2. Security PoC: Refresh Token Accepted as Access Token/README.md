## 2. Security PoC: Refresh Token Accepted as Access Token

### Overview
A critical vulnerability was identified where the system incorrectly accepts a `refreshToken` as a valid `accessToken` for authenticating requests to protected resources. This bypasses the intended security mechanism of having short-lived access tokens.

### Impact
This leads to an **Authentication Bypass**. If a `refreshToken` is compromised, an attacker can use it directly to access protected API endpoints, circumventing the intended short lifespan of access tokens and gaining unauthorized, potentially long-term, access to user accounts or system functionalities.

### Affected System
•   **System Type:** API authorization mechanism

•   **Sample Endpoint/URL:** `https://[anonymized-corporate-website.com]/api/protected-resource`

### Steps to Reproduce
1.  Perform a successful login to obtain both an `accessToken` and a `refreshToken` from the authentication response.
2.  Attempt to send a request to a protected API endpoint (e.g., `/api/protected-resource`) using the **`refreshToken`** in the `Authorization: Bearer` header, instead of the `accessToken`.
3.  Observe that the request is successfully processed, indicating the `refreshToken` was accepted as an `accessToken`.

### Proof of Concept
[Screencast 1: Authentication Bypass demonstrating refreshToken usage](https://youtu.be/JNT8FAChJgM)

### Tools Used
•   Postman
