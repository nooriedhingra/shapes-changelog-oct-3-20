# Shapes.inc Changelog - October 16, 2025

## Room Discovery with Upvote/Downvote System

Vote-based discovery for finding the best rooms.

**What's new:**
- Upvote/downvote rooms in directory
- Vote-based sorting (show highest rated first)
- Your votes are saved per-account
- Room score visible on cards

**How it works:**
- Browse /rooms directory
- Click ▲ to upvote (good room)
- Click ▼ to downvote (not for you)
- Sort by: Hot (votes), Recent (activity), New (created)

**Technical details:**
- Room votes table (user_id, room_id, vote)
- Real-time vote aggregation
- Vote-based ranking algorithm
- Prevents duplicate votes

**Why:**
Room directory had no quality signal. Upvotes surface the best rooms and help users find value faster.

---

## Shape Discovery with Upvote/Downvote System

Vote-based discovery for finding the best Shapes.

**What's new:**
- Upvote/downvote Shapes in directory
- Vote-based sorting (show highest rated first)
- Your votes are saved per-account
- Shape score visible on cards
- New modal for adding Shapes to rooms
- Footer on directory pages
- Better dark mode colors

**How it works:**
- Browse /shapes directory
- Click ▲ to upvote (good Shape)
- Click ▼ to downvote (not for you)
- Sort by: Hot (votes), Recent (added), Popular (usage)

**Technical details:**
- Shape votes table (user_id, shape_id, vote)
- Real-time vote aggregation
- Vote-based ranking algorithm
- Improved dark mode contrast for vote buttons

**Why:**
Shape directory had no quality signal. Upvotes surface the best Shapes and help users discover valuable AI companions.

---

## Voice Calls Status Indicators

See who's in voice calls directly from the sidebar.

**What's new:**
- Voice call indicator badge on sidebar rooms
- "In call" status shows participant count
- Click to join active call
- Real-time status updates

**Where you'll see it:**
- Sidebar room list (green phone icon)
- Room header (shows active call)
- Join button appears when call is active

**Technical details:**
- WebSocket-based status updates
- Batched voice status API calls (performance)
- Real-time participant tracking
- Efficient sidebar rendering

**Why:**
You couldn't tell if a voice call was active without opening the room. Now you can see and join calls at a glance.

---

## Voice Call UI Improvements

Better video call experience across devices.

**What improved:**
- Maximize video overlay size on desktop
- Fix video call toolbar on iOS
- Fix tile sizes for better layout
- Double tap to maximize video tile (mobile)
- Add banners to video tiles (show profile pics)

**Technical details:**
- Responsive tile sizing algorithm
- Touch gesture support (double tap)
- iOS-specific UI adjustments
- Optimized video rendering

**Why:**
Voice call UI wasn't optimized for different screen sizes. These fixes make calls look better and work smoother everywhere.

---

## Engagement Analytics & Database Indexes

Internal analytics improvements for understanding user behavior.

**What's new:**
- Comprehensive engagement metrics dashboard
- Message volume tracking
- Room activity metrics
- Shape interaction stats
- Database indexes for performance

**Technical details:**
- New database indexes on Message_v2 table (100M+ rows)
- Prevents 5-30s query times
- Optimized analytics queries
- Hybrid pre/post July 8 approach

**Why:**
Analytics queries were timing out on large tables. Indexes make dashboards fast and usable.

---

## Bug Fixes & UX Improvements

**Real-Time Sidebar Updates**

Sidebar now updates in real-time when:
- New messages arrive
- Rooms created/deleted
- Unread counts change
- Room activity updates

No more manual refreshes needed. Uses WebSocket events for instant updates.

**Fixed Shape Selection in Room Creation**

Composer doesn't auto-close after selecting a shape during room creation (was annoying).

**Improved Dark Mode for Upvoting**

Better contrast and colors for vote buttons in dark mode.

**Reddit Icon in Footer**

Added Reddit link to footer with proper FontAwesome icon.

**Mobile Voice Call Experience**

Improved mobile UX for voice calls:
- Better touch targets
- Responsive controls
- Cleaner layout on small screens

**Activity Indicator Timeout**

Increased timeout for "typing..." indicator (was disappearing too fast).

**Fixed `/create` Pill Parsing**

`/create` in messages no longer renders as a clickable pill (was confusing).

**Hide Premium Features During App Review**

Temporarily hid premium features for App Store review process.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
