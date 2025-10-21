# Shapes.inc Changelog - October 10, 2025

## Zoom Into Images

Click any image in chat to view it in fullscreen zoom mode.

**What's new:**
- Click image → fullscreen overlay
- Pinch/scroll to zoom in/out
- Tap outside to close
- Works on desktop and mobile

**Technical details:**
- New image viewer component with gesture support
- Preserves image quality at high zoom levels
- Smooth animations and transitions

**Why we built this:**
Screenshots, diagrams, and memes were too small to read in chat. Now you can inspect every pixel.

---

## UID Search in Moderation System

Super editorial staff can now search users by UID (user ID).

**What's new:**
- Moderation panel → three search modes: Email | Username | UID
- New API endpoint: `/api/users/search-by-uid`
- Updated `/api/moderation/user-chats` to accept `uid` parameter
- Works in both Rooms tab (find user chats) and Users tab (ban users)

**Why:**
Sometimes you only have a user ID from logs or reports. Now you can search by UID directly instead of hunting for email/username.

**Technical details:**
- Added UID search button to moderation UI
- Server-side UID lookup with error handling
- Documented in architecture notes

---

## Room Creation Flow Improvements

Cleaned up room creation modal (Step 3).

**What changed:**
- Fixed instruction modal placeholder bleeding
- Better text overflow handling
- Improved mobile responsiveness

**Before:** Placeholder text was bleeding outside the textarea.

**After:** Clean, contained placeholder text.

---

## Bug Fixes & UX Improvements

**Fixed Voice Messages Stopping When New Messages Come In**

Voice messages were pausing when new messages arrived in chat. Fixed audio player lifecycle to persist playback across message updates.

**Note:** YouTube embed player still has issues (tracked separately in CIR-4408).

**Fixed Forum Layout Bleeding (Again)**

More forum card layout fixes:
- Long titles/descriptions wrap properly
- No text overflow on mobile
- Cards maintain consistent height

**Fixed Rare Bleeding on Directory Interaction Modal**

Attempted blind fix for edge case where directory interaction modal text would overflow. Couldn't replicate locally but added overflow guards.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums or #suggestions!*