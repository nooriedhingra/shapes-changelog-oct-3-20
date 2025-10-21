# Shapes.inc Changelog - October 11, 2025

## Auth0 Session Duration Fix

Users were being logged out unexpectedly. Fixed session durations to keep you logged in.

**What changed:**
- **Rolling duration:** 100 days (max Auth0 allows)
- **Absolute duration:** 365 days (max Auth0 allows)
- Sessions auto-refresh on any visit

**User experience:**
- Stay inactive for up to **100 days** → still logged in
- Active users effectively **stay logged in forever**
- Maximum session life: **1 year absolute**

**Root cause:**
Session duration params weren't explicitly set in code. Env vars were set in Vercel but ignored because `initAuth0()` calls didn't include duration parameters.

**Solution:**
Explicitly set session params in all `initAuth0()` calls:
- `lib/session.ts`
- `app/(auth)/api/auth/login/route.ts`
- `app/(auth)/api/auth/callback/route.ts`
- `app/(auth)/api/auth/[auth0]/route.ts`

**Technical details:**
- Documented in `architecture/AUTH0_SESSION_DURATION_FIX.md`
- Aligned Auth0 dashboard settings to match code
- Reference: [Auth0 Session Lifetime Docs](https://auth0.com/docs/manage-users/sessions/configure-session-lifetime-settings)

**Why this matters:**
Users were getting logged out mid-conversation. Now you stay logged in as long as you're active.

---

## Rewards Deadline Timer Update + Bonus Banner

Updated rewards timer to match backend week changes and showed users a +24hr bonus extension.

**What changed:**
- Deadline timer now counts to **Monday 00:00 UTC** (was Sunday)
- Aligns with backend week bounds (Monday-Sunday weeks)
- Calculates `daysUntilMonday` correctly for all days

**Bonus Time Banner:**
Showed until **Monday Oct 13, 2025 00:00 UTC**:

```
┌──────────────────────────────┐
│ 🎁 Bonus! We gave you +24hrs │
└──────────────────────────────┘

   ~~3h 42m left~~  (strikethrough)
   1d 3h 42m left!  (new deadline)
```

**Psychology principles:**
- **Reciprocity:** "We gave you..." creates obligation to engage
- **Loss Aversion:** Shows what you would have lost (strikethrough)
- **Gain Framing:** Green banner = positive surprise
- **Urgency Maintained:** Still shows live countdown

**Technical details:**
- Green banner with gift emoji
- Old deadline crossed out in gray
- New deadline emphasized in bold
- Auto-disappeared after Oct 13
- Stored in localStorage

---

## Guard Emoji Picker Focus State

Fixed mobile keyboard spam when using emoji picker.

**What changed:**
- Emoji button and picker overlay tagged as "feature buttons"
- Prevents composer from stealing focus on mobile
- Desktop keydown replays skip picker container

**Technical details:**
- Added `data-prevent-composer-autofocus` to picker
- Documented in `architecture/MULTIMODAL_INPUT_PERF.md`

**Before:** Opening emoji picker on mobile triggered keyboard.

**After:** Emoji picker opens cleanly without keyboard interference.

---

*Shipped by the team at [shapes.inc](http://shapes.inc). Got feedback? Drop it in forums!*