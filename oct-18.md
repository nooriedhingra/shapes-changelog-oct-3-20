# Shapes.inc Changelog - October 18, 2025

## Per-Room Skills Configuration

Configure which Skills are enabled on a per-room basis.

**What's new:**
- Room settings → Skills tab
- Toggle individual Skills (web search, image gen, code, etc.)
- Skills respect room-level config
- Default: all Skills enabled

**How it works:**
- Room owner opens settings → Skills  
- Toggle Skills on/off for that room
- Shapes in that room only use enabled Skills
- Persisted in room metadata

**Technical details:**
- New room skills config system
- Frontend UI for toggling
- Backend respects room-level overrides
- Falls back to global defaults

**Why:**
Some rooms don't need all Skills (e.g., study room doesn't need image gen). Per-room config gives owners fine control.

---

## Shapes Chat Free Will Simplified

Removed confusing "free will" toggle, kept only reactions.

**What changed:**
- Removed "allow free will" setting
- Kept "allow reactions" toggle
- Cleaner room settings UI
- Simpler mental model

**Technical details:**
- Removed free will logic from backend
- Shapes only respond when mentioned (default)
- Reaction permissions still configurable

**Why:**
"Free will" was confusing users. Simplifying to mentions-only makes behavior predictable.

---

## Shape Directory Modal Improvements

Better UX for adding Shapes from directory.

**What's new:**
- DM and Dashboard buttons in Shape modal
- Fullscreen modal on smartphones
- Better touch targets
- Cleaner layout

**Technical details:**
- Mobile-responsive modal
- Added quick action buttons
- Improved touch hit areas

**Why:**
Adding Shapes from directory required too many clicks. New modal streamlines the flow.

---

## Room Directory Search Improvements

All room types now searchable via command palette.

**What's new:**
- Search includes: Favorites, Hidden, Community, DMs
- Room avatars in search results
- Favorites indicator (⭐)
- Better result grouping

**Technical details:**
- Unified search across all room types
- Client-side filtering
- Avatar rendering in dropdown
- Optimized query performance
- Fixed z-index bleeding

**Why:**
Search was missing hidden DMs and community rooms. Now it searches everything.

---

## Room-Level Credit Opt-Out UI

Protect your credits by opting out of premium usage in specific rooms.

**What's new:**
- Room settings → AI Configuration → "Don't Use My Credits"
- Toggle on: your credits won't be consumed in this room
- Toggle off: normal credit usage
- Per-room setting (not global)

**How it works:**
- Join premium room → credits normally consumed
- Enable opt-out for that room → credits protected
- Room still works (uses room owner's credits or community pool)

**Technical details:**
- New user-room credit opt-out table
- Backend checks opt-out before charging
- Apple-style toggle UI (simple + clear)
- Moved to AI configuration page

**Why:**
Users wanted to join premium rooms without spending credits. Opt-out lets you participate without financial risk.

---

## Bug Fixes & UX Improvements

**Fixed Banner Fallback Style**

Profile and room banners now properly fallback when no image set.

**Clean Debug Logs**

Removed all debug console.logs from production build.

**Stabilized Rooms Provider**

Backend stability improvements for room data fetching:
- Less errors
- Faster loads
- Better error handling

**Add Banners to Video Tiles**

Video call tiles now show user profile pictures when camera is off.

**Directory UI Improvements (Mobile)**

Smartphone optimizations:
- Better touch targets
- Responsive cards
- Fixed bleeding issues
- Improved scrolling

**Don't Show Community Rooms in Recent Rooms**

Community rooms no longer clutter "Recent Rooms" section on homepage.

**Hide Copy Request ID for Non-Editorial**

"Copy Request ID" debugging feature now only shows for editorial staff.

**Automatically Open Video Call Overlay**

When starting/joining a call, video overlay auto-opens (don't need to click separately).

**Unified Native-Style Share Dialog**

Redesigned share dialog:
- Native social platform support (WhatsApp, Twitter, Instagram, Snapchat, LinkedIn)
- Custom social icons
- Responsive layout
- Better deep linking
- Fixed room modal routing

**Fixed Participants Tab**

Room modal "Participants" tab now opens correctly (was broken, clicking did nothing).

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
