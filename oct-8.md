# Shapes.inc Changelog - October 8, 2025

## Community Forums

New community forums for posting feature requests, suggestions, and discussions.

**What's new:**
- Create discussion topics in `/forums`
- Browse "Latest" or "Top (7d)" threads
- Upvote forums and individual comments
- Threaded comment replies (max depth: 5 levels)
- Soft deletion with moderation checks
- Infinite scroll pagination

**How it works:**
- Click "Forums" in Shapes Community sidebar
- Create new thread → title + description
- Comment on threads, reply to comments
- Upvote/downvote posts and comments
- Delete your own threads, staff can archive any thread

**Technical details:**
- New tables: `forums`, `forum_comments`, `forum_votes`, `forum_comment_votes`
- Server-side helpers in `lib/forums-server.ts`
- API routes: `/api/forums`, `/api/forums/[slug]`, `/api/forums/[slug]/comments`, etc.
- SWR hooks for infinite feed and real-time vote updates
- Recursive comment tree rendering with optimistic updates

**Why we built this:**
Users were DMing us feature requests and filing GitHub issues for product feedback. Now there's a dedicated space for community-driven discussion and voting on what we should build next.

---

## Room-Level Multi-Message Toggle

Per-room control over whether AI Shapes can send multiple messages in a row.

**What's new:**
- Room settings → AI Settings → "Allow Multiple Messages" toggle
- Override Shape's default multi-message behavior
- Reset to Shape default with one click
- Works on room creation and cloned rooms

**How it works:**
- Each room can enable/disable multi-message mode independently
- Falls back to Shape's default if no override set
- Cloned rooms inherit source room's setting
- Real-time UI updates with optimistic rendering

**Technical details:**
- New column: `allowMultipleMessagesOverride` in `Chat` table
- Migration: `0063_allow_multiple_messages_override.sql`
- Exposed in room settings API (`/api/chat/[id]/settings`)
- Documented in `architecture/room-creation.md`

**Why:**
Some users wanted AI to send rapid-fire follow-ups in certain rooms but not others. Now you can configure this per room instead of per Shape.

---

## New Room Presets (Roleplay, Casual, Smart)

Added new preset categories with grouped selection UI.

**What's new:**
- **Smart presets:** Deep Research, etc.
- **Casual presets:** General chatting
- **Roleplay presets:** Character-based interactions
- Grouped preset selector in room creation dialog
- Preset picker in room AI settings modal
- Auto-loads preset instructions into textarea

**Technical details:**
- Presets defined in `lib/constants/room-presets.ts`
- Documented in `architecture/ROOM_SHAPE_SETTINGS.md`
- Updated room creation dialog (Step 4)
- Updated room AI settings modal

**Why:**
Users were confused by the flat list of presets. Grouping by category makes it easier to find the right starting point for your room.

---

## Participant Badges Refactor

Fixed badge rendering logic to account for visibility state.

**What changed:**
- Badges now respect participant visibility settings
- Fixed edge cases where badges weren't showing
- Improved performance by reducing unnecessary re-renders

**Technical details:**
- Refactored badge logic in participant components
- Added visibility checks to badge rendering pipeline
- Optimized with React memoization

**Before:**
Badges would sometimes disappear or show for invisible participants.

**After:**
Badges consistently render only for visible participants.

---

## Bug Fixes & UX Improvements

**Fixed Badges Not Showing Up Sometimes**

Participant badges were inconsistently rendering. Fixed race condition in visibility state checks.

**Fixed Variant Cycle Controls When No Labels**

Message variant cycling broke when messages had no labels. Now handles edge case gracefully.

**Removed "Logged Out Experience Coming Soon" Text**

Cleaned up logged-out view by removing placeholder text that was never implemented.

**Removed Sidebar Tools Setup**

Dropped "Tools" option from sidebar user menu now that Composio tools are deprecated. Also removed YouTube/Reddit authentication popup.

**Don't Render Media Links as Attachments in Reply Area**

Media link previews no longer show as attachment cards in "Replying to..." area. Cleaner UI, less clutter.

**Limited Max Height for Message Context Menu**

Message right-click menu was getting too tall with many options. Now scrolls after a certain height.

**Added Back Onboarding Modal (Commented Out)**

Re-added onboarding modal code (commented out) for future use. Not active yet.

**New Hook to Grab User-Owned Shapes**

Created `useUserOwnedShapes()` hook for fetching Shapes created by the current user. Powers upcoming Shape management UI.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions or the new forums!*