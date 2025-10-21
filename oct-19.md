# Shapes.inc Changelog - October 19, 2025

## Markdown Support in Room Descriptions

Room descriptions now support full Markdown formatting.

**What you can do:**
- **Bold**, *italic*, ~~strikethrough~~
- Links: [example](https://example.com)
- Lists (bulleted and numbered)
- Code blocks
- Headings

**Where it shows:**
- Room directory cards
- Room info modal
- Join page
- Room settings preview

**Technical details:**
- Uses same Markdown renderer as messages
- Sanitized HTML output (security)
- Preserves formatting in all views

**Why:**
Room descriptions were plain text only. Markdown lets you create better-structured, more informative descriptions.

---

## Room Templates Feature

Save room configurations as templates for quick reuse.

**How it works:**
- Room settings → "Save as template"
- Name your template
- Template saves: AI settings, permissions, moderation, skills
- Create new room from template in one click

**What gets saved:**
- Shape selections
- Room preset
- Custom instructions
- Skill toggles
- MCP servers
- Moderation settings (slow mode, banned words, etc.)
- Privacy settings

**Technical details:**
- New `room_templates` table
- Template creation/listing APIs
- One-click room cloning from template
- Documented in architecture notes

**Why:**
Power users were recreating the same room setup over and over. Templates let you reuse configurations instantly.

---

## Notification Preferences Granularity

More control over what notifications you receive.

**New settings:**
- DM notifications: All | Mentions only | None
- Room notifications: All | Mentions only | None
- Email notifications: Immediately | Daily digest | Never
- Shape activity notifications toggle

**Where to configure:**
Settings → Notifications

**Technical details:**
- Granular notification preferences in user profile
- Backend respects all preferences
- Real-time preference sync

**Why:**
All-or-nothing notification settings were too rigid. Now you can fine-tune exactly what you want to be notified about.

---

## Bug Fixes & UX Improvements

**Fixed Room Creation Modal Scroll**

Modal now properly scrolls on mobile when keyboard is open.

**Improved Markdown Rendering Performance**

Optimized Markdown parser for faster message rendering:
- ~30% faster parse time
- Better handling of large messages
- Reduced memory usage

**Fixed Shape Avatar Upload**

Shape avatar upload now properly validates image dimensions and file size.

**Improved Search Result Highlighting**

Search results now highlight matched keywords in yellow.

**Fixed Mention Autocomplete**

@ mention autocomplete now filters results as you type (was showing all users).

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*
