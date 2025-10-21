# Shapes.inc Changelog - October 9, 2025

## Rainbow Profile Picture Borders

Premium users can now show off with animated rainbow borders around their avatars.

**How it works:**
- Premium users automatically get rainbow border option
- Border shows everywhere: messages, profiles, sidebar, participant lists
- Smooth animated gradient effect
- Controlled via `UserAvatar` component (applies globally)

**Why we built this:**
Users wanted more ways to flex premium status. Rainbow borders are eye-catching without being obnoxious.

**Implementation:**
- CSS gradient animation on avatar wrapper
- Respects user's premium status from profile metadata
- No performance impact (GPU-accelerated)

---

## Display Name Styling Improvements

Display names now render with consistent styling across messages and profiles.

**What changed:**
- Display names use proper font weights and colors
- Consistent appearance in messages, chat headers, mentions
- Better readability in dark mode

**Note:** Some surfaces (chat header, mentions) still use old styling. Full rollout coming in next PR with shared component.

---

## Room Skills Settings Redesign (Stage & Save)

Completely redesigned how room owners manage Shapes skills, MCP servers, and webhooks.

**What changed:**
- New "stage then save" flow instead of instant updates
- Radio card selection style (matches multi-message UI)
- Toggle skills, MCP servers, webhooks in one pass → click Save
- Floating Save/Cancel toolbar stays visible while scrolling
- Draft state management shows pending changes

**Why the redesign:**
Old UI saved on every interaction, causing API spam and confusing state. New flow lets you preview changes before committing.

**How it works:**
1. Open Room AI Settings → Skills tab
2. Toggle core skills, MCP servers, or webhook groups
3. UI shows "dirty" state (unsaved changes)
4. Click Save to commit, or Cancel to revert

**Technical details:**
- Draft state in `room-ai-settings.tsx`
- Radio cards in `custom-tools-card.tsx`, `mcp-servers-section.tsx`, `shapes-tools-section.tsx`
- Dirty tracking callbacks report pending work to parent
- Architecture doc updated: `SHAPES_INC_UI_CHANGES.md`

---

## Premium Tags on Room Directory Cards

Room cards in the directory now show "Premium" or "Standard" badges.

**What you see:**
- Crown icon + "Premium" badge for sponsored rooms or premium-only rooms
- "Standard" badge for free rooms
- Shown on room cards in `/rooms` directory

**Why this matters:**
Users couldn't tell which rooms required premium or credits before clicking in. Now it's visible at a glance.

**Implementation:**
- `/api/featured-rooms` enriched with `hasPremiumCredits` and `isSponsored` flags
- Badge rendering in room directory cards
- No extra client fetches (data comes in initial load)
- Architecture doc: `room-directory-voting.md`

---

## Share to Room Directory

New "Room Directory" quick action in share dialog.

**How it works:**
- Open room share dialog
- Click "Room Directory" button
- Room gets listed in public directory (or refreshes if already listed)
- No need to navigate away from share modal

**Why:**
Users were confused about how to list rooms in the directory. Now it's one click from the share menu.

**Implementation:**
- Share dialog action button calls directory listing API
- Success toast confirms listing
- Architecture doc updated: room directory workflow

---

## Message Context Menu Improvements

Fixed UX issues with the message action menu (3-dot menu).

**What changed:**
- Menu now shows 4.5 items (not 4) to hint at scrollability
- Gradient fade at bottom indicates more options
- Reordered actions: high-frequency actions at top, destructive at bottom
  - New order: Edit, Regenerate, Reply, Copy, Chat now, Branch off, Delete, Report
- "Branch off" moved after "Chat now" (logical grouping)

**Why:**
Old menu showed exactly 4 items with no scroll indicator. Users didn't know there were more options. Reordering puts most-used actions within easy reach.

---

## DM Moderation Fixes

Fixed inappropriate moderation options showing in user DMs.

**What we fixed:**
- Removed "Kick" and "Ban" options from DM message menus
- "Delete" only shows for your own messages in DMs
- Server-side check enforces DM deletion rules (only author can delete)

**Before:**
DMs showed kick/ban/delete options for all messages (made no sense).

**After:**
DMs only show relevant actions (reply, copy, edit your own, delete your own).

**Technical approach:**
- Thread `isUserDM`/`isShapeDM` flags through message component
- API route checks `chat.chatType === 'user_dm'` before allowing deletion
- Architecture doc updated: `API_ROUTES_ALPHABETICAL.md`

---

## Slow Mode Persistence Fix

Fixed slow mode resetting when switching rooms.

**What was broken:**
Slow mode (rate limiting) would reset to 1 minute when you switched rooms, even if configured for 5 minutes.

**Root cause:**
Redis TTL was hardcoded to 60 seconds instead of using room's configured window.

**Solution:**
- Cache `roomWindowSeconds` during rate-limit check
- Forward window to `recordMessage` in Redis
- Use `Math.max(1, window)` when setting TTL
- Now persists correctly across room switches

**Implementation:**
- Updated `lib/rate-limiter.ts` to accept optional window param
- Architecture doc: `MODERATION_AND_BANS.md`

---

## Forums UI Fixes

Fixed layout issues on forums page (mobile + desktop).

**What we fixed:**
- Long forum titles/descriptions now wrap instead of bleeding off screen
- Whole forum card is tappable (except upvote button)
- Upvote button moved below summary for better touch targets
- Mobile sidebar trigger is proper square (was stretched)

**Before:**
Long titles would overflow, cards had dead zones, upvote button too close to text.

**After:**
Clean card layout, clear tap targets, proper text wrapping.

---

## Removed Legacy Code

**Room Shape Settings Collection Removed**

Deleted old `room-shape-settings` collection. Now relying on `room-shapes` only. Cleaner data model, less duplication.

**Create Room with "Chat Now" Dialog Fix**

Fixed broken "Create room with Shape" option in chat now dialog. Was throwing errors, now works correctly.

---

## User Engagement Tracking (Backend)

Added bulk user engagement tracking for analytics. Tracks message sends, room joins, Shape interactions. Frontend metrics coming next.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Drop feedback in [Forums](/forums)!*