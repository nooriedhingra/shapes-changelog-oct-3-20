# Shapes.inc Changelog - October 12, 2025

## Suggested Messages in New Rooms

AI-generated conversation starters appear in empty rooms to help you begin chatting.

**How it works:**
- Create/join room → Shape greeting appears
- 3 suggestion bubbles appear below greeting
- Click suggestion → fills input (doesn't auto-send)
- Edit before sending if you want
- After first message → suggestions disappear

**Key details:**
- Shows when **you** have 0 messages (unaffected by others' activity)
- Hides "@mention a shape" blue hint when suggestions visible
- Cached per room (no duplicate fetches)
- Graceful fallback if API fails

**Technical details:**
- Fetches 3 suggestions from `/api/messages/suggested-replies`
- Parallel API calls (3 requests simultaneously)
- Session-cached per room
- Documented in technical notes

**Why:**
Blank rooms are intimidating. Starter suggestions give users a nudge to begin conversations.

---

## Badge System Overhaul

Cleaned up how badges display across the app.

**What changed:**
- **Chat messages:** Show only top 1 badge (priority: team > sponsor > room > level)
- **Profile modal:** Show all applicable badges
- **Own messages:** Now show badges (previously hidden)

**New badges:**
- Level badges (e.g., "Shape Expert") now appear in profile modal
- Sponsor badges in profile modal (respects user preferences)
- Premium badge added

**Clickable badges:**
Badges are now clickable and navigate to relevant pages (e.g., rewards, profiles).

**Removed badge preferences:**
Badge preference UI was confusing and unnecessary. Now we auto-show only the highest priority badge in chat, and all badges in profile modal.

**Technical details:**
- Updated `hooks/use-participant-badges.ts` with priority logic
- Updated `components/profile-modal-content.tsx` to show all badges
- Added level fields to `EnrichedPillData` type
- Documented badge hierarchy

**Why:**
Badge clutter in chat was overwhelming. Now you see the most important badge inline, and can click profiles to see everything.

---

## Personas UI Improvements

Redesigned personas form with shapes.inc style.

**What changed:**
- Labels: "MY NAME" and "MY BACKSTORY" (was generic)
- Added helpful hint text for each field
- Updated placeholders with concrete examples (kpop stan, basketball player, etc.)
- Fixed textarea font size inconsistency (forced 14px)
- Cleaned up navigation (hid Chat Now, Profile, Copy link buttons on personas page)

**Technical details:**
- Updated base `Textarea` component font size
- Added `hideActions` prop to personas/settings pages
- Consistent typography matching `Input` component

**Why:**
Generic form labels didn't explain what personas do. New labels and hints make it obvious how to create good personas.

---

## Room Creation Modal UX Cleanup

Bunch of improvements to room creation flow.

**What changed:**

**Automatically scroll to top on step change:**
Modal now scrolls to top when you click Next/Back. No more mid-scroll step transitions.

**Removed 2nd back button:**
Had two back buttons (header + footer). Removed footer button, kept header button.

**Made upload boxes clickable:**
Picture icon boxes for profile/cover images now clickable. Before they were just decorative.

**Fixed ellipsis overflow on Step 2:**
Room name/description no longer overflows with "..." bleeding outside container.

**Removed helper text from multi-message feature box:**
Simplified UI by removing redundant explanation text.

**Improved Step 3 layout:**
Bunch of spacing and alignment fixes for better mobile experience.

**Show advanced section on Step 3:**
Advanced options (slow mode, etc.) now visible on Step 3.

**Technical details:**
- Updated `create-room-dialog.tsx` across multiple steps
- Scroll behavior via `scrollIntoView`
- Better conditional rendering
- All changes documented in Linear (CIR-4469)

---

## Move Private Account Toggle to Settings

Moved private account toggle from sidebar dropdown into Settings popup.

**Why:**
Sidebar dropdown was getting cluttered. Settings popup is the right place for account privacy controls.

**What changed:**
- Added private account toggle to `ui-settings-popup.tsx` with Shield icon
- Removed from `sidebar-user-nav.tsx` dropdown
- Same functionality, better location

---

## Improve Personas UI with Conditional Formatting

Personas now display with proper conditional formatting and spacing.

**Technical details:**
- Better card layouts
- Consistent spacing between persona cards
- Improved mobile responsiveness

---

## Bug Fixes & UX Polish

**Fixed Strikethrough Time Display in Rewards Modal**

Strikethrough value in bonus time banner now shows "0h 0m" when old deadline has passed (instead of showing negative time).

**Hide 'Configure Shapes' Option for Non-Owners**

Non-owner room members could see "Configure Shapes" in settings modal. Now properly hidden.

**Behavior:**
- User DMs: Hidden (no Shapes to configure)
- Shape DMs: Shown (you're always the owner)
- Multiplayer rooms: Only shown to owners

**Move 'Copy Message Link' to Bottom of Menu**

Message context menu action order updated:
- High-frequency actions (Edit, Regenerate) at top
- "Copy Message Link" moved to very bottom (below Delete, Report, Kick, Ban)

**Auto-Redirect Existing Participants from Join Page**

If you're already in a room and visit the join link, we now redirect you directly to chat instead of showing the join form.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*