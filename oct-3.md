# Shapes.inc Changelog - October 3, 2025

## Custom Sidebar Categories

Organize your rooms exactly how you want. Create custom categories, drag rooms into them, and keep your sidebar clean.

**How it works:**
- Right-click any room → "Move to category"
- Create new categories on the fly or choose existing ones
- Rename, reorder, or delete categories anytime
- Favorites and Shapes Community sections stay pinned at top
- Categories sync across all your devices

**Why we built this:**
Users with 50+ rooms needed better organization. Generic chronological lists don't scale. Now you can group work rooms, friend chats, or project spaces however makes sense to you.

**Implementation details:**
- New `user_sidebar_categories` table with user-specific sort order
- Optimistic UI updates keep sidebar responsive during network calls
- Modal on desktop, bottom sheet on mobile for category selection
- Rooms with categories filter out of default "Chats" section automatically

---

## Onboarding Flow Restored

The 3-step onboarding is back after a quick revert to fix auth bugs.

**What was fixed:**
- Auth0 session cookies were too large, causing header overflow errors
- Trimmed cached profile data to essential fields only
- Onboarding now completes without session corruption

**Onboarding steps:**
1. **Choose your vibe** — Roleplay, Smart, or Casual
2. **Discover Shapes** — Find Shapes that match your interests
3. **Complete profile** — Add pronouns, bio, avatar

Early data shows users who complete onboarding stick around 2.4x longer.

---

## Bug Fixes & Technical Improvements

**Auth0 Session Optimization**

Fixed a critical bug where users with long bios or metadata would hit 8KB cookie header limits and get logged out unexpectedly.

**Solution:**
- Sanitize Auth0 profile payload before caching in cookies
- Keep only essential fields (id, username, email, avatar)
- Reduced average cookie size by ~65%
- No more mysterious logouts for power users

**Voice Message URL Fix**

Voice messages now keep their playback URLs intact. Previously, our URL stripping logic would break voice message links, making them unplayable.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions.*