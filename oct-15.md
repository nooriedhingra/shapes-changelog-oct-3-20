# Shapes.inc Changelog - October 15, 2025

## Search Messages by Username

Search for messages from specific users in room search.

**How it works:**
- Room modal → Search → `from:username your search query`
- Filters messages by sender username
- Works with regular text search too

**Examples:**
- `from:noorie feature request` → messages from noorie containing "feature request"
- `from:biel bug` → messages from biel containing "bug"

**Technical details:**
- Added `from:` parsing to `/api/chat/[id]/search-messages`
- Resolves usernames through profile cache
- Documented in `architecture/API_ROUTES_ALPHABETICAL.md`

**Why:**
Users wanted to find messages from specific people in busy rooms. Now you can filter by sender.

---

## Search Only Executes on Submit

Room search now requires explicit submit (no more search-on-every-keystroke).

**What changed:**
- Type query → press Enter or click submit button
- Blue "Enter" icon button (CornerDownLeft)
- Search only fires when you submit
- Clear/reset still works instantly

**Why:**
Searching on every keystroke was hammering the API and showing irrelevant partial results. Now you control when search runs.

**Technical details:**
- Added state isolation for submitted searches
- New submit control in `components/chat-header.tsx`
- Documented in UI changes log

---

## Text-Based Commands Are Non-Sticky

Typing `!imagine` or `!web` now only applies to the current message, not follow-ups.

**How it works:**
- **Type !imagine:** Image mode for this message only
- **Click Image button:** Image mode stays active for follow-ups
- Same for !web and other commands

**Why:**
Users would type `!imagine` for one message, then forget it was still active. All future messages were interpreted as image prompts. Now typed commands are one-shot.

**Technical details:**
- Tracks how modifiers were enabled (typed vs button)
- Button-enabled modifiers persist
- Typed modifiers clear after send
- Documented in `architecture/SHAPES_INC_UI_CHANGES.md`

---

## Auto-Save Room Skills Toggle

Room skills toggle now auto-saves (removed Save/Cancel workflow).

**What changed:**
- Toggle skills on/off → saves instantly
- Removed floating Save/Cancel bar
- Loading state shows while saving
- Cleaner, faster UX

**Why:**
"Stage then save" workflow was overcomplicated for simple toggles. Auto-save is more intuitive.

**Technical details:**
- Removed draft state management
- Instant API calls on toggle
- Loading indicators during save
- Multiple Linear tickets resolved (CIR-4446, CIR-4447, CIR-4445, CIR-4444)

---

## Improved Persona Cards

Persona management cards redesigned for better readability.

**What changed:**
- Cards span full profile content width
- Instruction text in thin-scrollable viewport
- Single column layout
- Edit/delete actions aligned with default toggle on one row

**Before:** Cards were cramped, hard to read long instructions.

**After:** Full-width cards with scrollable instruction area, clean action row.

---

## Fixed Cmd+K Search Results

Command palette search was showing duplicate results. Fixed deduplication logic.

**What changed:**
- Dedupes results via shared helper
- Shape DM favorites merged ahead of other DMs
- Prevents duplicate room/DM suggestions
- Now includes Shapes Community category results

**Technical details:**
- Updated `components/command-palette.tsx`
- Documented in `architecture/COMMAND_PALETTE.md`

**Before:** Same room could appear multiple times in search results.

**After:** Each result appears once, favorites prioritized.

---

## Bug Fixes & UX Improvements

**Fixed Emoji Suggestion Panel Closing**

Emoji shortcode autocomplete (`:smile:`) now properly dismisses after typing a space. Before it would linger.

**Technical details:**
- Tracks when caret moves past token
- Clears state immediately on whitespace
- Documented in `architecture/MULTIMODAL_INPUT_PERF.md`

**Fixed Searching in Custom Sections**

Sidebar search now properly searches custom categories. Before it was skipping them.

**Fixed Voice/Audio Players with Context**

Fixed audio/voice message players using React Context to track playback state. Prevents players from unmounting when new messages arrive.

**No UI changes, just behavior fix.**

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*