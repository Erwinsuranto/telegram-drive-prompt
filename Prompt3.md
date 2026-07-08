```
Implement the complete Telegram Drive upload system.

Requirements:

Architecture
- Keep the current architecture.
- Telegram Channel stores all uploaded files.
- MongoDB stores metadata only.
- Never store binary files in MongoDB.
- Temporary local files must be deleted after successful Telegram upload.

Upload System
- Support any Telegram supported file.
- Maximum upload size follows Telegram limits.
- Generate unique downloadToken for every uploaded file.
- Store:
  - original filename
  - file size
  - mime type
  - telegram file_id
  - telegram message_id
  - uploader id
  - upload date
  - downloadToken
  - upload status
- Save metadata into MongoDB.

API
Create clean REST endpoints:
- POST /api/files/upload
- GET /api/files/:id
- GET /api/files/token/:downloadToken

Validation
- Validate file size.
- Validate mime type.
- Handle duplicate uploads.
- Handle upload interruption.
- Return structured JSON errors.

Logging
- Log every upload.
- Log failures.
- Log upload duration.

Code Quality
- Follow current project structure.
- Keep controllers, services, middleware and routes separated.
- Use async/await.
- Add comments only where necessary.

Testing
- Verify the upload flow.
- Verify metadata is stored correctly.
- Verify Telegram upload succeeds.
- Verify temporary files are deleted.

Documentation
Update README.md with upload API documentation.

Do not implement download, search, authentication, admin panel, website, force join, statistics, or frontend.

Stop after the upload system is complete and explain every created or modified file.

```
