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
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/51af971b-ec3c-4244-aebe-fe4f807d51b7" />
## 🔐 Auth Service (Microservice) + 🛒 Cart Service + 🚪 API Gateway + 🔑 JWT Authority = Clean Architecture
<img width="1642" height="770" alt="image" src="https://github.com/user-attachments/assets/d0563e60-a120-4fca-a95e-351844801f81" />
## Alot of layers 
<img width="750" height="799" alt="image" src="https://github.com/user-attachments/assets/2cc55ffb-49a7-4eac-9e78-c79ac280e8ce" />

