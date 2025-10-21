# Shapes.inc Changelog - October 19, 2025

## Unified Sidebar: Combined DMs and Rooms

Merged DMs and rooms into a single unified sidebar for simpler navigation.

**What changed:**
- One sidebar instead of two tabs
- All conversations (DMs + rooms) in one list
- Sorted by: Pinned → Recent activity → Alphabetical
- Cleaner, simpler mental model

**How it works:**
- Open sidebar → see all your chats
- DMs show user avatars
- Rooms show room avatars
- Both types mixed together by recency

**Technical details:**
- Unified data fetching
- Combined sorting algorithm
- Preserved pin/favorite state
- Optimized rendering performance

**Why:**
Switching between "DMs" and "Rooms" tabs was unnecessary friction. Unified sidebar puts everything in one place.

---

## Bug Fixes & UX Improvements

**Renamed "Channels" to "Rooms"**

Consistent terminology across the app. Everything is now called "rooms" (not channels).

**Fixed Skeleton Loading State**

Sidebar skeleton now matches actual content layout (less visual jump when loading).

**Improved Mobile Sidebar Performance**

Faster rendering on smartphones:
- Virtualized list for 100+ rooms
- Lazy avatar loading
- Reduced rerender cycles

**Fixed Search Modal Focus**

Search modal now properly focuses input on open (mobile + desktop).

**Improved Unread Badge Positioning**

Unread count badges now properly align on all avatar sizes.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
