# Shapes.inc Changelog - October 18, 2025

## Profile Page Performance Improvements

Optimized profile page loading and rendering.

**What changed:**
- Lazy load profile sections
- Reduced initial bundle size
- Faster time-to-interactive
- Better mobile performance

**Technical details:**
- Code splitting for heavy components
- Deferred non-critical data fetches
- Optimized image loading
- Documented in performance notes

**Results:**
- ~40% faster initial load
- Smoother scrolling on mobile
- Lower memory usage

---

## Improved Shape Discovery

Enhanced Shape discovery page with better filtering and search.

**What's new:**
- Category filters (Roleplay, Productivity, Creative, etc.)
- Sort by: Popular, Recent, Top Rated
- Search with autocomplete
- Featured Shapes section

**Technical details:**
- Updated discovery API
- Client-side filter caching
- Optimistic UI updates

**Why:**
Old discovery page was hard to navigate. New filters make it easy to find relevant Shapes.

---

## Bug Fixes & UX Improvements

**Fixed Chat Input Focus Issues**

Chat input no longer steals focus unexpectedly on mobile.

**Fixed Room Member List Sorting**

Member list now properly sorts by: Owner → Moderators → Members → Offline

**Improved Loading States**

Better loading indicators across the app:
- Skeleton screens instead of spinners
- Progressive content loading
- Smoother transitions

**Fixed Notification Badge Count**

Notification badges now accurately reflect unread count.

**Before:** Badge would show stale counts or not update.

**After:** Real-time accurate counts.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
