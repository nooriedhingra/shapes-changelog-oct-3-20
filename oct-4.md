# Shapes.inc Changelog - October 4, 2025

## Live Markdown Editor for Room Presets

Type room instructions in Markdown and see the formatting in real-time. No more toggling between edit and preview modes.

**What changed:**
- New `MarkdownTextarea` component replaces plain text fields
- Supports headings, lists, bold, italic, code blocks — all rendered as you type
- Works in both room creation flow and settings modal
- Auto-converts `# ` into styled headings, `- ` into lists, etc.
- "Escape space" lets you exit formatting blocks cleanly

**Why we built this:**
Room preset instructions are basically mini-docs. Asking users to write Markdown blind and hope it looks right is bad UX. Now you get instant feedback on structure and formatting.

**Technical approach:**
- Content-editable div, not a textarea — gives full control over rendering
- Parse Markdown blocks on keypress → inject styled spans
- Serialize back to canonical Markdown on blur
- Sentinel character (`\u200B`) manages caret position when exiting blocks
- Shared component used in `create-room-dialog.tsx` and `room-ai-settings.tsx`

**Architecture docs:**
Added `MARKDOWN_RENDERING.md` to cover inline formatting, block parsing, and escape behavior for future contributors.

---

## Clickable Message Labels → Premium Banners

"Premium Required" and "Credits Required" labels now open in-app upgrade banners instead of redirecting you to billing pages.

**What we fixed:**
- Labels dispatch `show-premium-banner-auto` event
- Banner reveals contextual upgrade flow: sponsored rooms → credits → premium
- No more jarring navigation out of chat
- Matches behavior of header upgrade buttons

**Why:**
Users were confused when clicking labels yeeted them to Stripe checkout. Keeping the flow in-app reduces friction and explains *why* they're seeing the label.

**Implementation:**
- `shapes-metadata-labels.tsx` — labels now clickable, fire custom event
- `chat.tsx` — listens for event, toggles correct banner state
- Removed `router.push('/pricing')` redirect logic

---

## Cycle Through Regenerated Messages

When you regenerate a Shape's response, you can now cycle through all variations without losing context.

**How it works:**
- Click regenerate → new response appears
- Arrow buttons let you navigate between all generated versions
- Each version preserves full context and metadata
- Works across all chat types (DMs, rooms, group chats)

**Why we built this:**
Users were frustrated losing good responses when regenerating. Now you can compare outputs, pick the best one, or reference earlier versions.

**Technical details:**
- New `message_variants` table tracks all regenerations per message
- UI shows variant counter (e.g., "2 of 5") when multiple exist
- Optimistic updates keep UI snappy during regeneration
- Variants tied to parent message ID for easy lookup

---

## UI Polish & Bug Fixes

**Compressed Badge Spacing**

User badges (Premium, Verified, etc.) now sit closer together. Looks cleaner, especially on mobile.

**Fixed Message Actions on Multi-Attachment Messages**

Reply/React/Delete icons were vertically misaligned on messages with multiple images. Now they anchor properly to the top-right.

**Fixed MCP Tool Editing**

MCP (Model Context Protocol) tools can be edited again. Bug was blocking users from updating tool definitions in settings.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions.*