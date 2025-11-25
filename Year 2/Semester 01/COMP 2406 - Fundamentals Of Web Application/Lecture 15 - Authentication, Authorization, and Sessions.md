
**Authentication (AuthN)** — _Who are you?_ Verifying identity (passwords, tokens, biometrics).
**Authorization (AuthZ)** — _What are you allowed to do?_ Checking permissions, roles, scopes.
**Sessions** — _How do we remember a client between requests?_ Mechanism (stateful or stateless) for maintaining continuity (e.g., cookies, tokens).

They’re related but distinct. Authentication proves identity; authorization decides access; sessions implement continuity of that identity across requests.


---
#### **Authentication (AuthN)**

##### Common Methods
1. **Username + Password**
    - Server verifies credentials.
    - Store passwords hashed (bcrypt, Argon2, scrypt) + salt.
2. **Token-based authentication**
    - Server issues a token after successful login (e.g., JWT, opaque token).
    - Client sends token in `Authorization` header or cookie.
3. **Session cookies**
    - Server creates a session record and sends a session id in an HTTP cookie.
4. **API keys**
    - Static keys tied to account (useful for machine-to-machine).
5. **OAuth 2.0**
    - Delegated access (common for third-party logins / APIs).
6. **OpenID Connect (OIDC)**
    - Identity layer on top of OAuth 2.0 — used for Single Sign On (SSO).
7. **Multi-Factor Authentication (MFA)**
    - Adds a second factor: TOTP apps, SMS (less preferred), hardware keys (U2F/WebAuthn).
8. **Passwordless**
    - Magic links, one-time codes, WebAuthn (strong, phishing-resistant).

##### Password handling — important rules
- Never store plaintext passwords.
- Use a slow, adaptive hash function (Argon2 > bcrypt > scrypt).
- Add a unique salt per user.
- Use a pepper (optional secret added on server) for extra safety.
- Rate-limit login attempts, lock accounts temporarily after retries.
- Enforce password complexity & optional password blacklists.

#### Example: Basic token flow
1. Client `POST /login` with credentials.
2. Server validates, issues token `{ access_token, refresh_token }`.
3. Client sends `Authorization: Bearer <access_token>` on protected requests.
4. When access_token expires, client uses refresh_token to get a new access_token.


---
#### **Authorization (AuthZ)**

##### Models of authorization
- **Role-Based Access Control (RBAC)**  
    Users are assigned roles (admin, editor). Roles map to permissions.
- **Attribute-Based Access Control (ABAC)**  
    Policies depend on attributes (user.age, resource.owner, time-of-day).
- **Access Control Lists (ACLs)**  
    Explicit lists on resources: who can read, write, execute.
- **Capability-based**  
    Tokens grant specific capabilities (e.g., presigned S3 URLs).

##### Scopes vs Permissions
- **Scopes** (OAuth): high-level rights granted to a client (e.g., `read:messages`).
- **Permissions**: finer-grained internal checks mapping to actions/resources.

##### Implementing authorization
- **Policy enforcement point (PEP)**: middleware that checks access for each request.
- **Policy decision point (PDP)**: service or module that evaluates policies (can be remote).
- Use least privilege: grant minimal permissions necessary.
- Log authorization failures for audit.

##### Example: Authorization check pseudocode:
```
def authorize(user, resource, action):
    if user.role == 'admin':
        return True
    if resource.owner_id == user.id and action in ['read','edit']:
        return True
    # check ACLs or ABAC policies...
    return False
```


---
#### **Sessions — stateful vs stateless**

##### Stateful sessions (server stores session)
- Server creates session record (in-memory, DB, Redis) with `session_id`.
- Server sends `Set-Cookie: session_id=abc123; HttpOnly; Secure; SameSite=Strict`
- On each request, client sends cookie; server looks up session and authenticates.
	**Pros**
	- Easy to revoke (delete session).
	- Server-side control over session lifetime and content.
	**Cons**
	- Server must store sessions (scaling requires distributed session storage).
	- Breaks strict REST statelessness (but still RESTful if server doesn’t store client app state).

##### Stateless sessions (self-contained tokens)
- Use JWT or opaque tokens where token carries or maps to identity.
- Server does not store session state for access tokens.
	**Pros**
	- Scales easily: no need for centralized session store.
	- Simple horizontal scaling.
	**Cons**
	- Harder to revoke (unless you implement token blacklists or short expiry + refresh).
	- If token contains sensitive claims, rotation/refresh must be handled carefully.

##### Hybrid approach
- Use **short-lived access tokens** (JWT) + **refresh tokens** stored server-side (stateful) or as long-lived rotating tokens (more secure). This balances stateless access and revocable sessions.


---
#### **Cookies vs Authorization header vs localStorage**

##### Cookies
A **cookie** (also known as a web cookie or browser cookie) is a small piece of data a server sends to a user's web browser. The browser may store cookies, create new cookies, modify existing ones, and send them back to the same server with later requests. Cookies enable web applications to store limited amounts of data and remember state information; by default the HTTP protocol is [stateless](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview#http_is_stateless_but_not_sessionless).

Typically, the server will use the contents of HTTP cookies to determine whether different requests come from the same browser/user and then issue a personalized or generic response as appropriate.

Cookies are mainly used for three purposes:
- **Session management**: User sign-in status, shopping cart contents, game scores, or any other user session-related details that the server needs to remember.
- **Personalization**: User preferences such as display language and UI theme.
- **Tracking**: Recording and analyzing user behaviour.

Pros: browsers send automatically; can be `HttpOnly` (unreadable by JS) and `Secure`.
Best for web apps where you protect against XSS (use `HttpOnly`) and mitigate CSRF (use `SameSite` or CSRF tokens).
- Example cookie attributes:
```
Set-Cookie: session=abc123; HttpOnly; Secure; SameSite=Lax; Path=/; Max-Age=3600
```

##### Authorization header (`Authorization: Bearer <token>`)
- Pros: clear separation from browser cookies; avoids CSRF (if not stored in cookie).
- Typically stored in memory or localStorage. **Storing in localStorage is vulnerable to XSS.**
- Recommended for single-page apps: prefer storing tokens in memory + refresh via secure cookies.

##### localStorage
- Easy to use, persists across refreshes — but **vulnerable to XSS**. Avoid for sensitive tokens.

##### Best practical approach for SPAs
- Store **refresh token in an HttpOnly, Secure cookie** (server issued).
- Keep **access token in memory** (short lived) and fetch new one using refresh endpoint (CSRF-protected).
- Or use the Authorization header approach with strong XSS protections.


---
#### **JWT (JSON Web Tokens)**

- Structure: `header.payload.signature` (base64url encoded)
    - Header: algorithm, type.
    - Payload: claims (`sub`, `exp`, `iat`, `iss`, custom claims).
    - Signature: HMAC or RSA signature.
- Example claims:
```
{ "sub": "42", "iss": "https://auth.example", "exp": 1610000000 }
```
- Use cases: stateless authentication, passing identity and simple claims.

**Practical cautions**
- **Do not** put sensitive info in JWT payload (it’s base64, not encrypted).
- Set **short expiry** (`exp`) for access tokens.
- For revocation: use short lifetimes + refresh tokens, or maintain a token revocation list (stateful).
- Validate signature, `iss`, `aud`, `exp`, `nbf` claims.


---
#### **OAuth 2.0 & OpenID Connect (OIDC) — quick guide**

##### OAuth 2.0 — principal flows
- **Authorization Code (with PKCE)** — recommended for SPAs & native apps (secure).
- **Authorization Code (server-side)** — recommended for server apps.
- **Client Credentials** — machine-to-machine (no user).
- **Implicit** — deprecated (unsafe for modern apps).
- **Resource Owner Password Credentials** — deprecated.

##### Authorization Code Flow (high-level)
1. Client redirects user to Authorization Server with client_id, redirect_uri, scope, state.
2. User authenticates on Authorization Server and consents.
3. Auth Server redirects back with `code`.
4. Client exchanges `code` for `access_token` (+ optionally `refresh_token`).
5. Client uses `access_token` to call resource server.

**PKCE (Proof Key for Code Exchange)** adds extra verification for public clients (SPAs, mobile apps).

##### OpenID Connect
- Adds `id_token` (JWT) that describes identity.
- Useful for SSO: you get authenticated identity and optionally profile info.


---
#### **Session & Token Security Best Practices**

##### Always:
- Use **HTTPS** for all auth endpoints.
- Use **HttpOnly** and **Secure** flags on cookies.
- Use **SameSite** cookie attribute (Lax or Strict) to mitigate CSRF.
- Use **short-lived access tokens** (minutes).
- Use **refresh tokens** with rotation and revocation.
- Use strong hashing for passwords (Argon2 recommended).
- Implement **rate limiting** and account lockouts for login endpoints.
- Log authentication and authorization events for audit.
- Use **MFA** for sensitive operations.
- Validate all tokens server-side: signature, audience, issuer, expiry.

##### Mitigations:
- **XSS** → sanitize inputs, use Content Security Policy (CSP), use HttpOnly cookies.
- **CSRF** → use SameSite cookies or anti-CSRF tokens for state-changing requests when using cookies.
- **Token theft** → short token lifetimes; rotate refresh tokens; device-based revocation.
- **Replay attacks** → use `jti` claim and maintain blacklist or use one-time tokens for sensitive flows.


---
#### **Token Revocation & Logout**

- For stateful sessions: delete server session (easy).
- For stateless JWTs: implement one of:
    - Short expiry + refresh token (server can revoke refresh tokens).
    - Maintain a blacklist/denylist of revoked `jti` values (stateful).
    - Use opaque tokens instead of JWTs (server checks token store).
- Always remove client-side tokens on logout:
    - Clear cookies, localStorage, memory.


---
#### **Common Pitfalls & Anti-patterns**

- Storing JWT in localStorage (XSS risk).
- Using long-lived access tokens w/o refresh or revocation.
- Not validating token signatures or claims.
- Storing too much data in JWT payload (bloating & privacy).
- Using unauthenticated endpoints for sensitive operations.
- Leaving admin endpoints unprotected.
- Using HTTP (not HTTPS) for auth flows.