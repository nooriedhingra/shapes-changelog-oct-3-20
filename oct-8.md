# Shapes.inc Changelog - October 8, 2025

## Community Forums

Launched community forums where users can post feature requests, suggestions, and discuss Shapes.

**What you can do:**
- Create discussion topics in /forums
- Browse "Latest" or "Top (7d)" threads
- Upvote forums and individual comments
- Reply in threaded comments (up to 5 levels deep)
- Delete your own threads or comments
- Editorial staff can archive entire forums

**How it works:**
- New "Forums" section in Shapes Community sidebar
- Create topic → add title + body → publish
- Comments nest recursively with vote counts
- Soft deletion preserves thread structure
- Moderation tools for editorial team

**Why we built this:**
Users were dropping feature requests in random rooms or DMing support. Now there's a dedicated space for product feedback and community discussion. Upvotes surface the most-wanted features.

**Technical details:**
- New database tables: `forums`, `forum_comments`, `forum_votes`, `forum_comment_votes`
- Server-side helpers in `lib/forums-server.ts` handle creation, commenting, voting, deletion
- SWR hooks (`use-forums.ts`) for infinite pagination and optimistic vote updates
- Recursive comment rendering with vote handling (`forum-comment-thread.tsx`)
- Alert dialogs for destructive actions (delete confirmation)
- Architecture doc: `architecture/forums.md`

**URLs:**
- Forum list: `/forums`
- Forum detail: `/forums/[slug]`

---

## Room-Level Message Grouping Toggle

Room owners can now override whether AI messages are grouped or sent individually.

**How it works:**
- New toggle in Room AI Settings: "Allow multiple messages"
- When enabled, AI can send multiple messages in a row (like a human conversation)
- When disabled, AI sends one consolidated response
- Overrides the Shape's default behavior for that room

**Why this matters:**
Some Shapes (e.g., roleplay characters) work better when they can send multiple short messages instead of one long block. Other rooms need concise single responses. Now you control it per-room.

**Implementation:**
- New column: `allowMultipleMessagesOverride` in `chats` table
- Migration: `0063_allow_multiple_messages_override.sql`
- Room creation/cloning inherits or copies the override
- Settings API validates boolean/null
- Message renderer respects override, falls back to Shape default
- Architecture doc updated: `architecture/room-creation.md`

---

## New Room Presets (Roleplay, Casual, Smart)

Expanded room preset library with grouped categories for easier selection.

**What's new:**
- **Roleplay presets:** Character-based interactions
- **Casual presets:** Relaxed, conversational AI
- **Smart presets:** Deep research, structured thinking
- Presets now grouped by category in UI
- Automatic textarea loading when you select a preset

**Where it shows up:**
- Room creation dialog (Step 1)
- Room AI settings modal (for existing rooms)

**Why:**
Users were confused by flat preset list. Grouping by use case makes it obvious which preset to pick.

**Technical approach:**
- Presets organized by category in `lib/constants/room-presets.ts`
- Grouped selector in `create-room-dialog.tsx` and `room-ai-settings.tsx`
- Architecture doc updated: `architecture/ROOM_SHAPE_SETTINGS.md`

---

## Participant Badge Visibility Refactor

Fixed badges not showing up consistently on user profiles and messages.

**What we fixed:**
- Refactored badge rendering logic to respect visibility settings
- Badges now consistently appear in messages, profiles, and participant lists
- No performance regression (checked rerender counts)

**Why this was broken:**
Badge visibility checks were scattered across components, causing race conditions. Now centralized.

---

## UI Improvements & Bug Fixes

**Removed "Tools Setup" from Sidebar**

Composio YouTube/Reddit connectors are gone, so we removed the "Tools" menu item from sidebar. Cleaner UI, less confusion.

**Reply Context No Longer Shows Media Attachments**

When replying to a message with images/videos, the reply context bar no longer renders full media previews. Just shows text content now. Cleaner, less distracting.

**Before:**
Reply bar showed full image previews, taking up tons of vertical space.

**After:**
Reply bar shows "Replying to [username]: [text]" without media bloat.

**Message Context Menu Max Height**

Context menu (right-click on messages) now has max height and scrolls. No more menus extending off-screen on mobile.

**Variant Cycle Controls Fix**

Fixed regenerate variant arrows not showing when message has no labels. Now works correctly.

**Removed "Logged Out Experience Coming Soon" Text**

Cleaned up placeholder text on logged-out landing page.

**Onboarding Modal Commented Out (Hotfix)**

Temporarily disabled onboarding modal due to bug. Will re-enable after fix.

**New Hook: `use-user-owned-shapes`**

Added hook to fetch Shapes owned by a specific user. Used for profile pages and Shape management.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Post it in the new [Forums](/forums)!*