**Login Flow**

* User submits credentials → Frontend sends `POST /api/login`.
* Backend validates against the database, issues a JWT and a refresh token.
* Tokens are returned to the frontend, which stores them (e.g. in `localStorage` or an HttpOnly cookie).

**Protected API Call**

* When “Add to Cart” is triggered, the frontend includes the header

  ```
  Authorization: Bearer <JWT>
  ```
* The JWT middleware (e.g. `@jwt_required`) decodes the token, checks its `exp` and `role` claims, then hands off to the protected route’s logic.

**Refresh Token**

* If the JWT has expired (response 401), the frontend automatically calls

  ```
  POST /api/refresh
  ```

  including the refresh token.
* The backend verifies the refresh token, issues a new JWT, and the frontend updates its storage with the new token.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f27c8fae-524f-4493-adb3-1b67f4ea9d1a" />
