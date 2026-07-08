```
You are continuing the Telegram Drive project.

IMPORTANT:
- Continue from the current GitHub repository.
- Do NOT recreate existing features.
- Do NOT modify Upload, Download, Search, or Delete systems unless required.
- Preserve the current architecture.
- Keep MongoDB as metadata storage only.
- Telegram Channel remains the only binary storage.

Your task is to implement a complete Authentication & Session System.

Requirements:

1. User Registration
- Register with username, email, password.
- Validate all inputs.
- Email must be unique.
- Username must be unique.
- Hash passwords using bcrypt.

2. User Login
- Login using username or email.
- Generate JWT access token.
- Secure session handling.
- Token expiration.
- Logout endpoint.

3. User Profile
- Get current user profile.
- Update profile.
- Change password.
- Avatar URL field.
- Storage usage statistics.
- Uploaded file count.

4. Middleware
- JWT authentication middleware.
- Authorization middleware.
- Role middleware.
- Guest middleware.

5. Security
- Password hashing.
- JWT verification.
- Rate limiting for login.
- Input validation.
- Sanitize user input.
- Prevent duplicate registration.

6. API Endpoints

POST /api/auth/register
POST /api/auth/login
POST /api/auth/logout
GET /api/auth/me
PUT /api/auth/profile
PUT /api/auth/password

7. Documentation
Update README.md with:
- Authentication flow
- JWT usage
- Example requests
- Example responses
- Error codes
- Security notes

8. Testing
Provide curl examples.
Provide JSON examples.
Verify no existing feature is broken.

Rules:
- Do not remove any existing functionality.
- Follow current folder structure.
- Reuse existing utilities whenever possible.
- Write clean production-ready code.
- Explain what files were created or modified.

```

