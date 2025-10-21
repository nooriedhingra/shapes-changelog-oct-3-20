# Shapes.inc Changelog - October 16, 2025

## Prevented Double-Send of Voice Messages on Mobile

Fixed bug where voice messages would send twice on mobile devices.

**What was happening:**
- Record voice message on mobile → sends twice
- Created duplicate messages in chat
- Confusing for users and recipients

**Root cause:**
Mobile touch events were firing both `touchend` and `click`, triggering send twice.

**Solution:**
- Debounce send logic
- Track send state to prevent duplicate submissions
- Mobile-specific event handling

**Technical details:**
- Updated voice message component
- Added send state guard
- Documented in mobile interaction notes

---

## Improved Custom Instructions UX

Moved custom instructions to bottom of interface and increased height for better usability.

**What changed:**
- Custom instructions field now at bottom of chat settings
- Increased textarea height (3 → 5 lines visible)
- Better mobile layout
- Removed markdown formatting (plain text only)

**Why:**
Custom instructions were hidden in the middle of settings. New placement makes them more discoverable and easier to edit.

**Technical details:**
- Updated room AI settings layout
- Simplified instruction input (no markdown parser)
- Consistent with other long-form text inputs

---

## Typing Indicator Auto-Cleanup Extended to 60m

Extended typing indicator timeout from 30 minutes to 60 minutes with updated documentation.

**What changed:**
- Typing indicators now persist for 60 minutes before auto-cleanup
- Updated docs and comments
- More forgiving for slow typers / long-form messages

**Why:**
30-minute timeout was too aggressive. Users writing long messages would see typing indicator disappear mid-composition.

**Technical details:**
- Updated Redis TTL logic
- Documented in `architecture/TYPING_INDICATORS.md`

---

## Skill Preset Automation (Frontend)

New UI for managing automated skill presets in room settings.

**What's new:**
- Preset dropdown for common skill combinations
- One-click skill configuration
- Presets include: Code Assistant, Research, Creative Writing, etc.
- Save custom presets

**Technical details:**
- Frontend UI shipped
- Backend automation logic coming next
- Documented in skills architecture

---

## Locked Rooms Feature

Room owners can now lock/unlock their rooms to prevent new participants from joining.

**How it works:**
- Room settings → Lock toggle
- Locked rooms show 🔒 icon in directory
- New users can't join locked rooms
- Existing participants unaffected
- Editorial rooms can be locked by staff

**Why we built this:**
Room owners wanted to pause growth or limit rooms to existing members without making them private.

**Technical details:**
- New `isLocked` column in rooms table
- Lock status shown in directory cards
- Join page blocks new participants
- Lock/unlock API route
- Documented in architecture notes

---

## /purge Command

New moderation command for bulk message deletion.

**How it works:**
- Type `/purge @username 50` → deletes last 50 messages from that user
- Type `/purge 100` → deletes last 100 messages from anyone
- Only room owners and moderators can use
- Confirmation modal before deletion

**Technical details:**
- New command handler in moderation system
- Batch deletion API
- Audit logging for purge actions
- Documented in moderation commands

**Why:**
Moderators needed faster way to clean up spam or inappropriate content. Manual deletion was too slow.

---

## Commands Menu Reordering

Reorganized command menu for better discoverability.

**New order:**
1. /imagine (most used)
2. /web
3. /purge
4. /slowmode
5. /ban
6. /kick

**Why:**
Old alphabetical order buried frequently-used commands. New order prioritizes by usage frequency.

---

## Refactored User Message Notifications

Backend improvements for notification delivery.

**What changed:**
- Cleaner notification dispatch logic
- Better error handling
- Suppressed errors in user DM notification flows
- More reliable delivery

**Technical details:**
- Updated notification service
- Added fallback logic for failed sends
- Documented in `architecture/NOTIFICATIONS.md`

---

## Bug Fixes & UX Improvements

**Fixed Shape Name Prefix Duplication**

Assistant messages were showing redundant prefixes. Example: "Claude: ✅" now shows as just "✅".

**Before:** Message showed Shape name twice (in metadata AND in message body).

**After:** Shape name only in metadata, message body clean.

**Auto-Collapse Long Messages**

Long messages (>500 chars) now automatically collapse with "Show more" button.

**Why:** Massive walls of text were overwhelming chat. Now they're hidden by default.

**Hidden Emoji Icon on Mobile**

Emoji picker button now hidden on mobile (keyboard emoji picker is better UX).

**Fixed Typing Indicator PFP Redirect**

Clicking profile picture in typing indicator no longer incorrectly redirects to shapes.inc. Now goes to user profile.

**Reverted Shape Reply Style Toggle**

Rolled back experimental reply styling due to user feedback.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
