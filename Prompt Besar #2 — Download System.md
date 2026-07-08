```
Implement the complete Telegram Drive download system.

Requirements

1. Keep the existing architecture.
2. Use Telegram Channel as the only file storage.
3. Use MongoDB only for metadata.
4. Never store downloaded files permanently.

Download Features
- Download using downloadToken.
- Validate token before download.
- Support direct file streaming.
- Support resume for large files if possible.
- Update download counter.
- Record last download time.
- Record downloader information if available.
- Return proper HTTP status codes.

Security
- Reject invalid tokens.
- Reject deleted files.
- Reject unavailable Telegram messages.
- Prevent path traversal.
- Add rate limiting for download endpoint.
- Validate every request.

API
Create:
GET /api/download/:downloadToken
GET /api/files/:downloadToken/info

Metadata
Update:
- downloadCount
- lastDownloadAt
- lastDownloader
- downloadHistory

Logging
Log:
- successful download
- failed download
- response time
- Telegram API errors

Testing
Verify:
- valid download
- invalid token
- deleted file
- Telegram unavailable
- metadata updates correctly

Documentation
Update README.md and create DOWNLOAD_SYSTEM.md.

Do not implement search, authentication, admin panel, website, statistics dashboard, or frontend.

Stop after the download system is complete and explain every modified file.

```
