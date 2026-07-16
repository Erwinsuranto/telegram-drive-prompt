










# Prompt: Fix Mobile Layout Overlap (Telegram Drive)
```


You are a senior Next.js + React + Tailwind CSS engineer.

The mobile UI has serious layout issues.

Current problems:

1. "Shared with me" and "Collaborate" chips overlap the Telegram Drive header.
2. The slide menu overlaps the My Files page content.
3. Header spacing is incorrect on mobile.
4. Navigation drawer is not positioned correctly.
5. Elements stack on top of each other.

Your task is to fix the layout WITHOUT changing backend logic.

Requirements

## Header

- Telegram Drive logo must always be fully visible.
- Header must never be covered.
- Respect mobile safe-area.
- Add correct top spacing.

## Shared with me

- Remove floating position.
- Never render above the header.
- If these buttons are part of the file toolbar, move them below the page title.
- Otherwise hide them on mobile.

## Side Menu

When menu opens:

- Display as a Drawer.
- Slide from the right.
- Position: fixed.
- Top aligned below the header.
- Height:
  calc(100vh - headerHeight)

The drawer must never cover:

- Header
- Search box
- My Files title

Instead:

Overlay only page content.

## Z-index

Create a clean layer order.

Header
z-50

Drawer
z-40

Content
z-10

Floating buttons
z-20

Never use random z-index values.

## My Files

Keep layout:

Header

↓

Toolbar

↓

Search

↓

Sort

↓

Files

↓

Floating buttons

Nothing may overlap.

## Mobile

Test widths:

320px

360px

390px

412px

430px

768px

No horizontal scrolling.

No overlapping.

No clipped content.

## CSS

Remove any:

position:absolute

negative margin

translateY hacks

hardcoded top values

that cause overlap.

Use flex/grid and proper spacing instead.

## Final verification

✓ Header always visible

✓ Shared with me no longer overlaps

✓ Drawer opens correctly

✓ Drawer does not cover header

✓ My Files layout clean

✓ Upload button still works

✓ Responsive

✓ No TypeScript errors

Output:

- Every modified file.
- Root cause.
- Exact fixes applied.
- Before/after explanation.



```
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
