# Shapes.inc Changelog - October 5, 2025

## User Personas

Create custom AI personas that shape how Shapes talk to you across all your rooms.

**What you can do:**
- Create multiple personas (e.g., "Coding buddy", "Therapist", "Dungeon Master")
- Set a default persona for all rooms
- Override persona per-room in AI settings
- Edit/delete personas anytime from `/u/[username]/personas`
- No character limits on persona instructions (was 1000, now unlimited)

**How it works:**
- New sidebar menu item → "Personas" (UserCog icon)
- Create persona → set instructions → star to make default
- Room settings → "Personal AI" tab → choose persona override
- Room creation flow → Step 4 lets you pick persona
- Instructions apply to all AI responses in that room

**Data flow:**
Room-specific persona → Default persona → None

**Why we built this:**
Users were copy/pasting the same instructions into every room. Now you define personas once and reuse them everywhere. Power users can have different personas for work vs. roleplay vs. casual chat.

**Technical details:**
- New API routes: `/api/user/personas`, `/api/user/personas/[personaId]`, `/api/user/room-persona-preferences/[roomId]`
- `usePersonaPreferences()` hook with SWR caching
- Persona data stored in user doc, room preferences in room doc
- Real-time updates across all tabs
- Backend PR shipped in parallel to app repo

---

## What's New Modal

Replaced the always-visible announcements banner with a dismissable "What's New" modal.

**What changed:**
- Modal shows latest product updates on first login
- Dismiss button → stays dismissed
- Stored in localStorage, respects user's session state
- Only reappears when we ship new updates

**Why:**
The old banner was always there, annoying users who'd already seen the content. Modal gives more control — you can read updates when *you* want, not when we force them on you.

**Bug fixes:**
- Fixed modal popping up on every app load (wasn't waiting for loading state)
- Fixed dismiss state not persisting (localStorage race condition)
- Now waits for auth load before checking dismiss state

---

## Smart Room Presets Redesign

Completely redesigned how users pick room templates when creating a room.

**What's new:**
- Use case determines default preset (e.g., "Roleplay" → casual preset, "Work" → smart preset)
- Added "Deep Research" preset to Smart category
  - 5-step research process: TDP, MIG, CAS, RG, IR
  - Academic-grade citations and bias mitigation
  - Structured reporting with transparent methodology
- Added "Uncensored Mode" preset to Casual category
  - No content restrictions
  - Direct, unfiltered responses
- Removed confusing "✓ Recommended for smart rooms" label
- Cleaner UI with preset categories (Smart, Casual, Roleplay)

**Technical approach:**
- `create-room-dialog.tsx` → Step 1 use case selection sets default preset
- Presets now organized by category in constants file
- Free will behavior no longer tied to preset selection
- User can still override any preset after selection

---

## Collapsed Sidebar Shows Unread Items

When you collapse sidebar sections, unread rooms still show up (Slack/Discord style).

**How it works:**
- Click chevron to collapse "Chats", "Rooms", or custom categories
- Unread items remain visible even when collapsed
- Full functionality preserved (navigation, context menus, etc.)
- Clean way to hide noise while tracking important convos

**Implementation:**
- New `unreadPreview` prop on `SidebarSection` component
- Applied to `SidebarRooms`, `SidebarChats`, `SidebarCustomCategories`
- Filters unread items and renders them inline when collapsed
- No layout shift — smooth animation

**Why:**
Users with 50+ rooms were collapsing sections but losing track of new messages. Now you can minimize clutter without missing notifications.

---

## Rewards System (Frontend)

First version of our rewards program UI. Earn points for activity, unlock perks.

**What shipped:**
- Rewards page showing point balance and available rewards
- Track progress on challenges (e.g., "Send 100 messages")
- Visual indicators for unlocked rewards
- Integration with user profile

**How it works:**
- Points awarded for actions (messages sent, rooms joined, referrals)
- Redeem points for credits, premium features, or cosmetic unlocks
- Backend calculates points, frontend displays them

**Note:** This is v1 — backend logic still rolling out, so points may not update in real-time yet. Full system goes live next week.

---

## Bug Fixes & UX Improvements

**Removed Display Name Alert Modal**

Killed the annoying modal that warned users their display name might be an email address. Nobody liked it.

**Fixed Time Toggle Description**

Room settings → Time toggle now has correct description text. Was showing placeholder copy.

**Deep Research Preset Added to Smart Category**

New preset for academic-level research with citations and methodology tracking.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions.*