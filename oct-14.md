# Shapes.inc Changelog - October 14, 2025

## Block DMs Feature

Block users from sending you DMs. Full directional DM blocking system.

**How it works:**
- Block someone → they can't DM you, you can't DM them
- Block from message menu (3-dot menu → "Block user")
- Block from chat header (DM settings → "Block user")
- Blocked DMs show banner: "You've blocked this user" / "This user has blocked you"
- Composer disabled in blocked DM threads
- Super editorial staff can still view blocked threads (for moderation)

**Technical details:**
- New table: `user_dm_blocks` with directional blocking
- New API route: `/api/dm-blocks`
- Server utilities in `lib/dm-blocks-server.ts`
- Migration: `0065_user_dm_blocks.sql`
- Enforced at DM creation and message send
- Documented in `architecture/user-dm-privacy.md`

**Why we built this:**
Users needed a way to stop unwanted DMs without reporting or blocking the person entirely. Directional blocking gives you control.

---

## Moderation: Deleted Room Access & Badge

Super editorial staff can now access deleted rooms and see "Deleted" badges in moderation UI.

**What's new:**
- Deleted flag in moderation APIs
- "Deleted" badge shows on moderation panel
- Super editorial can view deleted rooms on chat page
- Room info API allows access for staff

**Why:**
Moderators needed to review deleted rooms for investigations. Now they can access deleted content without restoring it.

**Technical details:**
- Updated moderation APIs
- Added deleted badge UI component
- Documented in architecture notes

---

## Room Creation Flow Polish (Final Cleanup)

Massive UX cleanup for room creation modal.

**What shipped:**

**Removed Advanced Section:**
Advanced options (slow mode, etc.) removed from creation flow. Too distracting. You can still configure these in room settings after creation.

**Only Show Persona for Roleplay Users:**
- Persona feature now only shows for "Roleplay" use case
- Appears at top of Step 4 (not bottom)
- Hidden for "Casual" and "Smart" use cases

**Why:** Personas are primarily for roleplay. No need to confuse other users.

**Updated Starter Suggestions Logic:**
- Reduced from 3 suggestions → 1 suggestion
- Fixed detection logic to only show in truly empty rooms
- Now checks for ANY user messages (not just senderId match)
- Less aggressive, better UX

**Technical details:**
- Changed from 3 parallel API calls → 1 single request
- Simplified conditional logic
- Updated docs in `architecture/starter-suggestions.md`

---

## Room Directory Improvements

**Removed Upvoting:**
- No more upvote buttons on room cards
- No upvote counts displayed
- Cleaner, simpler directory UI

**Why:** Upvoting was creating perverse incentives (vote manipulation, etc.). We're moving to activity-based ranking instead.

**Activity-Based Sorting (Attempted):**
Tried switching directory sorting from upvotes → last activity. Ran into issues, reverted for now. Will re-ship with proper fix.

**Room Directory Sorting Fix (Final):**
- Removed pagination (show all rooms at once)
- Fixed sorting with SQL subquery: `MAX(message.createdAt)`
- Sort ALL rooms by fresh message time BEFORE limiting
- Removed ~70 lines of client-side re-sorting code
- Fixed timezone bugs (added `AT TIME ZONE 'UTC'`)

**Before:** Paginated first (using stale `lastActivity`), then re-sorted client-side. Recent rooms hidden on page 2+.

**After:** SQL sorts by actual latest message time, no pagination needed.

**Timezone fix:** Timestamps now show "7 hours ago" instead of "in about 7 hours" (was showing future time due to timezone parsing).

**Reverted again:** Had to revert this change (PR #1852) due to performance issues. Will re-ship optimized version.

**Load 100 Rooms at a Time (Not 20):**
Increased room directory load limit from 20 → 100 rooms per fetch for better performance.

---

## Bug Fixes & UX Improvements

**Fixed Batch Voice Status Endpoint N+1 Queries**

Voice status checks were causing N+1 database queries. Created batch request handler to fix performance.

**Filtering Out Global Banned User Messages**

Messages from globally banned users now filtered out of chat history.

**Added Deleted Variant to Banned User Modal**

Banned user modal now shows "Deleted" state for users who deleted their accounts.

**Fixed Display Level for Rewards**

Rewards modal was showing incorrect level display. Fixed calculation logic.

**Hide Web and Image Buttons in Human DMs**

User DMs (`chatType === 'user_dm'`) no longer show:
- Web search button
- Image generation button

These features only make sense with AI Shapes, not human-to-human DMs.

**Technical details:**
- Gated button render with `chatType !== 'user_dm'`
- Preserved all other composer functionality

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*