# Shapes.inc Changelog - October 17, 2025

## Real-Time Sidebar Activity Updates

Sidebar now updates in real-time for all room activity.

**What's new:**
- Unread indicators update instantly
- Room list reorders on new messages
- DM notifications appear immediately
- No manual refresh needed

**How it works:**
- WebSocket events for all room changes
- Real-time unread count tracking
- Automatic room list sorting
- Instant UI updates

**Technical details:**
- Migrated from polling to WebSocket
- Global event system for room updates
- Optimized rerender logic
- Fixed timezone handling for timestamps
- Simplified last-seen tracking

**Why:**
Sidebar was stale and required manual refresh. Real-time updates make chat feel alive and responsive.

---

## Readme Channel Feature

New special channel type for room documentation.

**What's new:**
- Readme tab in room header
- Markdown-formatted room documentation
- Edit access for room owners/mods
- Always visible to all room members

**How it works:**
- Room settings → Enable Readme
- Create/edit Readme content
- Shows as tab in room header
- Supports full Markdown formatting

**Technical details:**
- New Readme block type
- Stored in room metadata
- Markdown renderer (same as messages)
- Permission-based editing

**Why:**
Rooms needed persistent documentation for rules, guides, FAQs. Readme channel provides dedicated space for this.

---

## @everyone Mention Support

Mention all room participants at once.

**What's new:**
- Type `@everyone` to mention all members
- Shows in mentions inbox for all participants
- Only room owner can use (prevents spam)
- Highlighted in yellow like regular mentions

**How it works:**
- Type `@everyone` in message
- All room participants get mention notification
- Appears in mentions inbox
- Click to jump to message

**Technical details:**
- New mention type in markdown parser
- Special notification handling
- Permission check (owner only)
- Highlighted rendering

**Why:**
Room owners needed way to notify all members for announcements. @everyone solves this.

---

## Shape Directory UI Improvements

Better Shape discovery experience.

**What improved:**
- Do not format shape directory URLs as pills (cleaner)
- Fixed Shape card layout
- Better dark mode colors
- Add return button on directory pages
- Create/add Shapes modal improvements

**Technical details:**
- URL parsing improvements
- Dark mode color adjustments
- Modal UX enhancements

**Why:**
Shape directory had small UI issues making it hard to use. These fixes polish the experience.

---

## Bug Fixes & UX Improvements

**Room Search Fullscreen on Mobile**

Room search modal now opens fullscreen on smartphones (was tiny and hard to use).

**Fixed Incorrect Room Pill Rendering**

Room links in messages now render correctly as pills (was showing raw URLs sometimes).

**Fixed Video Call Toolbar on iOS**

iOS video call toolbar now shows properly (was cut off at bottom).

**Double Tap to Maximize Video Tile**

Double tap any video tile to maximize it (mobile gesture support).

**Show Activity Status for Shapes**

Shapes now show "Active", "Idle", or "Offline" status in sidebar and participant list.

**Increased Activity Indicator Timeout**

"Typing..." indicator now persists longer (less flickering).

**Improved Upvoting Dark Mode Colors**

Better contrast for vote buttons in dark mode (green/red more visible).

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
