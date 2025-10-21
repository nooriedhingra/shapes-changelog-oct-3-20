# Shapes.inc Changelog - October 6, 2025

## Profile Navigation Buttons

Added prev/next navigation buttons to user profiles so you can browse through profiles without going back to search results.

**How it works:**
- View any user profile from search, room members, etc.
- Arrow buttons (← →) appear in header
- Click to cycle through the list you came from
- Maintains search context and position
- Works on mobile and desktop

**Why we built this:**
Users browsing Shapes in discovery or checking out room members had to constantly back out and re-enter profiles. Now you can flow through profiles like a carousel.

**Technical details:**
- Navigation state stored in URL params (prev/next user IDs)
- `useProfileNavigation()` hook tracks list context
- Prefetches adjacent profiles for instant navigation
- Falls back gracefully when navigation context unavailable

---

## Photos & Videos in What's New Modal

Announcements now support image and video attachments in the What's New modal.

**What changed:**
- `/api/announcements` returns attachment payloads
- Normalized attachments in `useWhatsNew` hook
- Rendered with shared `PreviewAttachment` component
- Preserves existing scroll behavior

**Why:**
Product updates often need screenshots or demos to make sense. Text-only announcements felt incomplete.

**Implementation:**
- Reused message attachment rendering logic
- Added attachment support to announcements schema
- Documented in `MESSAGE_ATTACHMENTS.md` architecture doc
- Works with images, videos, and GIFs

---

## Mobile Suggestions UX Fix

Fixed annoying mobile behavior where tapping the suggestions button would auto-focus the input and pop up the keyboard.

**What we fixed:**
- Tapping suggestions trigger no longer refocuses textarea
- Soft keyboard stays closed when browsing suggestions
- Outside-click handling collapses suggestions picker cleanly
- Added test ID for focus logic verification

**Why this mattered:**
Mobile users were getting keyboard spam every time they wanted to browse Shape suggestions. Now the suggestions panel opens without keyboard interference.

**Technical approach:**
- Adjusted mobile focus guards in `multimodal-input.tsx`
- Added outside-tap dismissal to `suggestions-button.tsx`
- Documented refined mobile suggestion behavior in `MULTIMODAL_INPUT_PERF.md`

---

## Removed Legacy Free-Will Reactions

Cleaned up old reaction system that was replaced by server-side `SHAPES_CHOOSE_REACTION` tool.

**What we removed:**
- Client-side free-will reaction service
- Legacy tooling lookups
- Redundant reaction fetching logic

**What replaced it:**
- Server-side reaction handling via `SHAPES_CHOOSE_REACTION`
- Cached Shape categories to avoid repeated fetches
- Cleaner, more reliable reaction flow

**Why:**
Old system was causing race conditions and duplicate reactions. New system is faster, more consistent, and easier to maintain.

---

## Bug Fixes & UX Polish

**Fixed Timezone Bug in Weekly L-ness Frequency Display**

Week start dates were showing one day earlier due to timezone conversion. Database showed "Monday, October 6" but UI displayed "Sunday, October 5."

**Root cause:** `new Date("2025-10-06")` was parsed as UTC midnight, then converted to local timezone (PDT), shifting the day back.

**Solution:** Changed parsing from:
```typescript
const weekDate = new Date(week);
```
To:
```typescript
const weekDate = new Date(week + 'T00:00:00');
```

Now parses as local midnight instead of UTC. Week dates match user expectations.

**Fixed Placeholder Text in Create Room Modal**

Placeholder text on Step 4 of room creation was hidden behind the input box. Now properly visible inside the text field.

**Shared Activities/Artifacts Proposal Document**

Added initial outline for shared activities feature (whiteboards, code editors, etc.). Still in proposal phase — more details coming.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions.*