# Shapes.inc Changelog - October 7, 2025

## Editorial-Only Model Override Control

Editorial room owners can now prevent users from overriding the room's default AI model.

**What changed:**
- New "Prevent model overrides" toggle in room settings (editorial-only)
- When enabled, users can't change the model via chat header dropdown
- Auto-upgrade toggle also gated behind editorial permissions
- `prevent_model_overrides` column added to rooms table

**Why we built this:**
Editorial teams curating official Shapes want users to experience the intended model (e.g., Claude Sonnet for creative writing, GPT-4 for technical support). Letting users override breaks the curated experience.

**Implementation:**
- Backend: `prevent_model_overrides` column exposed through room settings API
- Frontend: Toggle visible only to editorial owners in room settings
- Gated auto-upgrade toggle updates behind editorial permissions
- Model dropdown hidden when override prevention is active

**Use cases:**
- Official Shapes Rooms (e.g., "Shapes Support") enforce GPT-4o
- Roleplay rooms enforce Claude Sonnet for personality consistency
- Educational rooms enforce specific models for curriculum

---

## Ban Users by Username (Proactive Moderation)

Room moderators can now ban users by username *before* they join the room.

**How it works:**
- New "Ban by username" input field in moderation settings
- Enter any username → user is banned from joining or posting
- Banned users list now shows both display names and usernames
- Ban actions tolerate already-absent users (no more spurious errors)

**Why this mattered:**
Previously you could only ban users who were already in the room. If someone was harassing across multiple rooms, mods had to wait for them to join before banning. Now you can proactively ban known bad actors.

**Technical details:**
- `/api/chat/[id]/banned-users` enriches results with display names + usernames
- `use-room-settings` hook added reusable banned-user refresh logic
- Manual ban helper resolves IDs via canonical username endpoint
- Ban actions from message menus tolerate missing users (no flow breakage)
- Architecture doc updated: `MODERATION_AND_BANS.md`

**Moderation flow:**
1. Enter username in ban field
2. System looks up user ID
3. Adds to room's banned list
4. User can't join or post in that room anymore
5. Banned list refreshes automatically

---

## Download Button for Chat Attachments

Added download button for non-media file attachments (PDFs, text files, etc.).

**What changed:**
- Download icon appears on file attachments in messages
- Click to download `.pdf`, `.txt`, `.docx`, and other document types
- Images and videos still preview inline (no download button needed)

**Why:**
Users couldn't download files sent in chat without right-clicking and "Save As." Now it's one click.

**Implementation:**
- New download button component in attachment preview
- Uses browser download API with filename preservation
- Only renders for non-preview-able file types

---

## Private Shape Owner Fanclub Fix

If a Shape owner's account is private, they're no longer automatically added as fanclub owner.

**What we fixed:**
- Fanclub ownership logic now filters out private Shape owners
- When all official owners are private, fanclub ownership goes to the visitor who requested it
- Prevents private accounts from leaking into public fanclub membership

**Why this mattered:**
Private accounts being auto-added to fanclubs exposed their existence in member lists. Now privacy settings are respected.

**Technical approach:**
- `shape-fanclubs-server.ts` filters owner IDs via `batchGetPublicUserProfileByUserIdServer`
- Falls back to requestor for new fanclub rooms when all owners are private
- Session data passed to fanclub helper to identify requestor

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions.*