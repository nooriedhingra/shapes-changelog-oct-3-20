# Shapes.inc Changelog - October 9, 2025

## Room Skills Settings Redesign

Completely redesigned room skills/tools settings with a "stage, then save" workflow.

**What changed:**
- Old: Toggles saved instantly, confusing UX
- New: Stage all changes → click Save → changes commit

**How it works:**
- Radio-style card selection for enabling/disabling:
  - Master skills toggle
  - Individual Shape skills
  - MCP servers
  - Webhook groups
- Floating Save/Cancel bar stays visible while scrolling
- Dirty state tracking shows unsaved changes
- All changes apply atomically on Save

**Technical details:**
- Draft state management for staged edits
- Card-based UI matching multi-message toggle design
- Local enablement drafts with dirty tracking callbacks
- Documented in `architecture/SHAPES_INC_UI_CHANGES.md`

**Why:**
Users were confused when toggles saved instantly. "Stage then save" gives you control — review all changes before committing.

---

## Share Rooms to Directory

Added "Room Directory" quick action to share dialog.

**What's new:**
- Share dialog → "Room Directory" button
- List your room in the public directory
- Refresh directory listing without leaving modal
- One-click publish/unpublish

**How it works:**
- Click share icon → "Room Directory" option
- Room gets listed in `/directory`
- Owners can update directory listing anytime

**Technical details:**
- Integrated into existing share dialog component
- Uses directory API (`/api/featured-rooms`)
- Documented in `architecture/room-directory-voting.md`

**Why:**
Users were asking "how do I list my room in the directory?" Now it's one click from the share menu.

---

## Premium Tag on Room Directory Cards

Room cards in the directory now show "Premium" or "Standard" badges.

**What's new:**
- Crown icon badge on premium rooms
- "Standard" badge on non-premium rooms
- Badges show in directory feed and search results

**How it works:**
- Directory API includes `hasPremiumCredits` and `isSponsored` flags
- Cards render badge based on premium status
- No extra client fetches needed

**Technical details:**
- Added premium metadata to `/api/featured-rooms`
- Updated directory card UI component
- Documented in `architecture/room-directory-voting.md`

**Why:**
Users wanted to know which rooms had premium features before joining. Now it's visible upfront.

---

## Rainbow Profile Picture Borders

Added rainbow animated borders for profile pictures (cosmetic unlock).

**What's new:**
- Rainbow gradient border animation on user avatars
- Applied automatically across entire app
- Shows on messages, sidebar, profiles, etc.

**How it works:**
- `UserAvatar` component renders rainbow border
- Animation loops continuously
- Visible everywhere avatars appear

**Technical details:**
- CSS gradient animation
- Applied at component level, propagates globally

**Why:**
Fun cosmetic feature for premium users or special achievements. More customization options coming.

---

## Display Name CSS Improvements

Fixed display name styling across the app.

**What changed:**
- Display names now render consistently with proper truncation
- Fixed overflow issues in message headers
- Improved readability with better spacing

**Note:** Display names not yet updated in chat headers, mentions, and other places. Full rollout coming in next PR.

---

## Bug Fixes & UX Improvements

**Improved Chat Menu Scrollability and Action Order**

Message context menu (3-dot menu) improvements:
- Shows 4.5 items instead of 4 → clearer scroll affordance
- Added gradient fade to indicate more options
- Reordered actions by priority:
  - High-frequency actions (Edit, Regenerate) at top
  - Destructive actions (Delete, Report) at bottom
  - "Branch off" moved after "Chat now"

**Before:** Menu showed exactly 4 items, users didn't know there were more options.

**After:** Partial 5th item visible with gradient fade, better action hierarchy.

**Fixed Forums Page Layout Bugs**

- Long forum titles/descriptions now wrap properly (no more text bleeding)
- Entire forum card is tappable (except vote button)
- Upvote button moved below summary for better UX
- Sidebar trigger is now a proper square on mobile

**Fixed Create Room With "Chat Now" Dialog**

Room creation from "Chat Now" dialog was broken. Fixed initialization flow.

**Removed Room Shape Settings Collection**

Cleaned up redundant data structure. Now relying solely on `room-shapes` collection for Shape settings.

**Fixed Slow Mode Reset on Room Switch**

Slow mode was resetting when switching rooms. Fixed Redis TTL to persist per-room slow mode windows.

**Technical details:**
- Cached `roomWindowSeconds` during rate-limit check
- Updated `recordMessage` to accept optional window parameter
- Documented in `architecture/MODERATION_AND_BANS.md`

**Don't Show Kick/Ban/Delete in User DMs**

Message context menu in user DMs no longer shows:
- Kick/Ban options (never made sense in DMs)
- Delete option (unless it's your own message)

**Fixed:**
- Server-side auth check for DM message deletion
- Client-side menu logic hides irrelevant actions
- Documented in `architecture/API_ROUTES_ALPHABETICAL.md`

**Tracking User Engagement in Bulk**

Added bulk user engagement tracking for analytics. Batches user activity events for better performance.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions or the forums!*