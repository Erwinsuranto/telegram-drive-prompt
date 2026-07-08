```
Implement only the Delete File backend.

Requirements:
- Create DELETE /api/files/:downloadToken
- Delete only files uploaded by the owner.
- Remove metadata from MongoDB.
- Delete the Telegram message if possible.
- If Telegram deletion fails, keep metadata status as "orphaned".
- Return clean JSON responses.
- Log every delete action.
- Do not modify Upload, Download or Search.
- Do not implement frontend.
- Update README only if API changes.
- Stop after Delete File is completed and explain modified files.

```

