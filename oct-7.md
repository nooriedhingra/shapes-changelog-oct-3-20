# Shapes.inc Changelog - October 7, 2025

## Download Button for Chat Attachments

Added download button for non-media file attachments (PDFs, text files, etc.) in chat messages.

**What's new:**
- Download icon appears on file attachments
- Click to download files directly
- Works for `.txt`, `.pdf`, `.doc`, and other document types
- Media files (images/videos) still use preview mode

**Why we built this:**
Users were right-clicking and "Save As..." to download files. Now it's one click.

**Implementation:**
- New `DownloadButton` component in attachment preview
- Conditional rendering based on file type
- Uses browser download API for client-side file handling

---

## Removed Suggestions Button from Message Actions

Cleaned up message actions by removing the suggestions button (wand icon) that appeared on every message.

**What changed:**
- No more wand icon in message action bar
- Suggestions still accessible via main input suggestions button
- Cleaner message UI with fewer icons

**Why:**
The per-message suggestions button was rarely used and cluttered the interface. Users prefer the global suggestions picker in the input area.

---

## Removed Obsolete Room Creation Presets

Cleaned up room creation flow by removing outdated preset options.

**What we removed:**
- "Just Chatting" preset
- "Casual (Uncensored)" preset
- Other legacy presets that weren't being used

**What stayed:**
- Smart presets (Deep Research, etc.)
- Active casual/roleplay presets
- Custom preset creation

**Why:**
Preset bloat was confusing new users. We consolidated to the most popular options and removed duplicates.

---

## Bug Fixes & Performance

**Optimized Attachment Rendering**

Improved performance for messages with multiple attachments by optimizing re-renders and caching attachment metadata.

**Fixed Edge Case in Profile Navigation**

Profile prev/next buttons now handle edge cases where navigation context is missing (e.g., direct profile URL visits).

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in #suggestions.*