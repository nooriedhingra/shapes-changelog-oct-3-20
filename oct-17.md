# Shapes.inc Changelog - October 17, 2025

## Improved Room Search with Debouncing

Room search now debounces input to reduce unnecessary API calls.

**What changed:**
- 300ms debounce on search input
- Fewer API requests while typing
- Faster, smoother search experience
- Loading indicator during debounce

**Why:**
Search was firing on every keystroke, causing API spam and stuttery UI. Debouncing batches requests for better performance.

**Technical details:**
- Uses `useDebouncedValue` hook
- 300ms delay (sweet spot for perceived responsiveness)
- Documented in search architecture

---

## Fixed Message Attachment Preview Rendering

Fixed edge cases where image/video attachments wouldn't preview properly.

**What we fixed:**
- Attachments with unusual MIME types now preview correctly
- Better fallback for unsupported formats
- Consistent preview behavior across all message types

**Technical details:**
- Updated attachment preview component
- Added MIME type validation
- Graceful degradation for unknown types

---

## Bug Fixes & UX Improvements

**Removed Legacy Notification Code**

Cleaned up old notification system code that was replaced by new architecture.

**Improved Error Messages**

Better error messaging throughout the app:
- More specific error descriptions
- Helpful suggestions for resolution
- Less technical jargon

**Fixed Sidebar Scroll Position**

Sidebar now properly maintains scroll position when switching rooms.

**Before:** Sidebar would jump to top every time you switched rooms.

**After:** Sidebar stays at your scroll position.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
