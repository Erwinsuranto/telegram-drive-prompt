
#Prompt: Restore Upload & Download Buttons (Telegram Drive)
```


You are a senior Next.js + React + Tailwind engineer.

The Upload page was accidentally modified.

Current situation:
- Route /upload still works.
- The page title "Upload" is visible.
- Description "Choose My Files to manage uploads." is visible.
- However, the Upload and Download buttons have disappeared.

Your task is to restore the previous functionality WITHOUT changing any existing backend logic.

Requirements:

1. Restore the Upload button.
   - Large primary button.
   - Opens file picker.
   - Supports drag & drop.
   - Uses existing upload API.
   - Show upload progress.
   - Mobile friendly.

2. Restore the Download button.
   - Display directly below Upload (not on the same row).
   - Use existing download logic.
   - Keep previous styling if available.
   - Mobile friendly.

3. Do NOT create new APIs.
   Use existing upload/download functions.

4. Search the project for previous Upload and Download components.
   Reuse them instead of rewriting.

5. If the buttons disappeared because of conditional rendering:
   - Fix the condition.
   - Remove incorrect hidden state.
   - Ensure buttons always appear.

6. If the buttons disappeared because of CSS:
   - Restore visibility.
   - Remove display:none, hidden, invisible or opacity issues.

7. Keep current design.
   Do not redesign the page.

8. Verify:
   ✓ Upload button visible.
   ✓ Download button visible.
   ✓ Upload works.
   ✓ Download works.
   ✓ Responsive on mobile.
   ✓ No TypeScript or ESLint errors.

Before finishing:
- Search git history if available.
- Search all Upload page commits.
- Restore missing JSX instead of creating fake placeholders.

Output:
- List every modified file.
- Explain why the buttons disappeared.
- Show the exact fix.



```
