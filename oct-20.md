# Shapes.inc Changelog - October 20, 2025

## Voice Channels (Alpha)

Launched alpha of voice channels for real-time voice chat in rooms.

**What's new:**
- Room owners can enable voice channel
- Join/leave voice channel with one click
- See who's in voice (live participant list)
- Mute/unmute yourself
- Push-to-talk mode
- Desktop + mobile support

**How to enable:**
Room settings → Features → Enable voice channel

**Current limitations (alpha):**
- Max 10 participants per voice channel
- No screen sharing yet
- No recording
- Desktop Chrome/Edge recommended (best experience)

**Technical details:**
- WebRTC peer-to-peer connections
- Fallback to SFU (selective forwarding unit) for larger rooms
- Voice activity detection
- Noise suppression
- Echo cancellation

**Why we built this:**
Text-only rooms were limiting for real-time collaboration. Voice adds new dimension for brainstorming, gaming, study sessions, etc.

**Roadmap:**
- Screen sharing (coming next week)
- Recording & transcription
- Spatial audio
- Video support

---

## Rich Text Composer (Beta)

New rich text editor for composing messages (opt-in beta).

**What's new:**
- WYSIWYG formatting toolbar
- Format as you type: **bold**, *italic*, `code`
- Drag-and-drop link previews
- Inline emoji picker
- Slash commands menu
- @ mention autocomplete

**How to enable:**
Settings → Experiments → Enable rich text composer

**Technical details:**
- Built on Lexical (Meta's text editor framework)
- Markdown export/import
- Mobile keyboard support
- Undo/redo history

**Why:**
Markdown is powerful but has learning curve. Rich text editor gives you formatting controls without memorizing syntax.

**Note:** This is opt-in beta. Default composer still uses Markdown. Feedback welcome!

---

## Shape Analytics Dashboard

Shape owners can now see analytics for their Shapes.

**What you can track:**
- Total messages sent by your Shape
- Active users (daily/weekly/monthly)
- Retention rate
- Average session length
- Top rooms using your Shape
- User ratings & feedback

**Where to access:**
Shape profile → Analytics tab (Shape owners only)

**Technical details:**
- Privacy-preserving analytics (no individual user tracking)
- Aggregated metrics only
- 90-day data retention
- Exportable reports

**Why:**
Shape creators wanted to understand how their Shapes are being used. Analytics help you improve your Shape based on real usage data.

---

## Bug Fixes & UX Improvements

**Fixed Message Edit History**

Message edit history now properly shows all revisions with timestamps.

**Improved Mobile Navigation**

Mobile bottom nav now highlights active tab correctly.

**Fixed Room Invite Links**

Invite links now properly preserve room context when shared.

**Improved Shape Response Time**

Optimized AI routing for ~20% faster Shape responses on average.

**Fixed Attachment Upload Progress**

Upload progress bar now accurately reflects upload status (was jumping around).

**Improved Dark Mode Contrast**

Adjusted dark mode colors for better readability:
- Higher contrast text
- Softer backgrounds
- More distinct UI elements

---

## What's Next (Coming Soon)

- Voice channel screen sharing
- Rich text composer general availability
- Room analytics for room owners
- Advanced moderation tools
- Custom emojis per room
- Threaded replies

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums or DM us!*
