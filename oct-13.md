# Shapes.inc Changelog - October 13, 2025

## Reverted Voice Message Fix

Reverted PR #1800 (voice message playback fix) due to unintended side effects.

**What happened:**
- Original fix stopped voice messages from pausing when new messages arrived
- Caused issues with other media players (YouTube embeds, etc.)
- Reverted to investigate proper solution

**Status:**
Voice message playback issue still being worked on. Will ship proper fix soon.

---

## Added chatId Parameter to Suggested Replies

Suggested replies API now accepts `chatId` parameter for better context-aware suggestions.

**Technical details:**
- Updated `/api/messages/suggested-replies` endpoint
- Suggestions now account for room context
- Better quality suggestions based on room history

**Why:**
Generic suggestions weren't relevant to specific rooms. Now suggestions adapt to the conversation context.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*