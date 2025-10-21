# Shapes Product Changelog
**October 3-20, 2025**

---

## 🎨 Rewards & Customization

### Message Bubble Effects & Styles
We've introduced a complete visual customization system for your messages:

**New Bubble Styles** (800 diamonds each):
- **Rectangular**: Clean, modern rectangular bubbles
- **Zigzag**: Playful zigzag edges
- **Jagged**: Edgy, rough-cut style
- **No Bubble**: Minimal text-only display

**New Message Effects** (1000 diamonds each):
- **Zombie**: Spooky green effects for Halloween vibes
- **Halloween Haunt**: Orange & black seasonal theme
- **Romantic**: Soft pink hearts and glows
- **Ice**: Cool blue frozen effects
- **LOL**: Fun bouncy animations for laughs

**How it works:**
- Purchase effects/styles in the Rewards Store
- Set your preferred style in Settings → Message Appearance
- Shapes automatically detect keywords and apply effects (e.g., typing "lol" triggers LOL effect)
- Toggle "Effects off" if you prefer clean messages
- Your chosen style appears on all your messages across all rooms

**Profile Modal Gradients** (1200 diamonds):
- Premium gradient backgrounds for your profile modal
- Multiple gradient options to choose from
- Shows when anyone views your profile

**Weekly Community Tasks:**
- New weekly task: "Leave a detailed review" for bonus diamonds
- Complete community tasks to earn rewards faster

**Pricing Updates:**
- Bubble styles: 800 diamonds
- Message effects: 1000 diamonds  
- Reaction packs: 500 diamonds
- Shape Credits: 10 diamonds = 1 credit

---

## 🤖 AI & Shape Improvements

### Alive Mode (Auto-Nudge)
Shapes can now work on long-running tasks without stopping:

- **What it does**: Automatically nudges shapes to keep working when they go idle for >5 minutes
- **How to enable**: AI Configuration → Toggle "Alive Mode"
- **How it works**: Server-side cron runs every 5 minutes, sends "Keep going - don't stop..." when shapes go idle
- **Perfect for**: Research tasks, multi-step projects, extended coding sessions
- **Works even when**: Your browser tab is closed

### Custom Instructions Improvements
Better experience for writing detailed shape instructions:

- **Larger editor**: Custom instructions field now has document-editor height (400px)
- **Bottom placement**: Moved to very bottom of AI Configuration for focus
- **Plain text**: Removed markdown processing for better performance
- **No more bugs**: Fixed weird newline issues with long instructions

### Message Quality Polish
Cleaner, more natural shape responses:

- **Removed timestamp artifacts**: No more "(Just now)" or "(2m ago)" in messages
- **Removed name prefixes**: Shape messages no longer say "Claude: your message"
- **Fixed URL stripping**: Voice message links now work correctly
- **Better formatting**: Messages look more natural and human-like

### Auto-Collapse Long Messages
Messages over 800 characters now auto-collapse for better readability:

- Shows preview of ~600 characters
- Clean "Show more/less" button with fade effect
- Works in light/dark mode
- **Exception**: Roleplay users see full messages (no collapse)

---

## 🛠️ Skills & Tools

### Editable Skill Instructions
You can now customize how skills behave in your rooms:

- **Where**: Room Settings → Skills → Click any skill
- **What**: Edit instructions for individual skills/toolkits
- **Reset**: One-click reset to default instructions
- **Applies to**: Both Shapes toolkits and member-connected tools

### Skill Preset Automation
New room presets that auto-configure skills:

- **What**: Pre-configured room templates with skills already set up
- **How**: Select skill-focused presets when creating rooms
- **Saves time**: No manual skill configuration needed

---

## 🏠 Room Management

### Room Cloning Improvements  
When you branch off a room:

- **MCP configs now clone** (but only for room owners)
- **Non-owners**: Can still clone message history
- **Preserves**: All your connected tools and configurations

### Room Branding Fixes
Fixed room icon/banner display logic:

- **Before**: Rooms with 1 shape would override custom branding with shape's avatar
- **Now**: Custom room icons/banners always show when set
- **Fallback**: Single-shape rooms show shape avatar only if no custom branding

### Invite Flow Improvements
Better experience for users joining via invite links:

- **Personal room created**: New users still get their own room
- **But redirected**: Lands you in the invite room after signup
- **Best of both**: You get your personal space + join the community

### Room Locking (Moderation)
Room owners can now lock rooms to prevent new members:

- **Lock toggle**: Room Settings → Moderation → Lock Room
- **When locked**: Invite links don't work, join requests blocked
- **Who can see**: Super editorial staff can still view locked/deleted rooms
- **Use case**: Pause community growth, handle moderation issues

---

## 💬 Messages & Chat UX

### TikTok Link Previews
TikTok links now show rich preview cards:

- Video thumbnail
- Title
- Author name
- Matches YouTube/Twitter preview style

### Voice Message Improvements
Fixed multiple voice message bugs:

- **No double-send**: Added loading state prevents accidental double-clicks on mobile
- **Continuous playback**: Voice messages don't stop when new messages arrive
- **Better UX**: Shows "Sending..." with spinner during upload

### Reply & Threading
Better reply experience:

- **Fixed scroll button**: No longer overlaps with reply close button
- **Dynamic positioning**: Scroll button moves up when reply is active

### Message Actions Menu
Cleaner, more organized message options:

- **Better scrollability**: Shows 4.5 items with fade gradient
- **Reordered**: High-use actions (Edit, Regenerate) at top
- **Copy link moved**: Now at very bottom after all destructive actions

---

## 🎯 Room Creation Flow

### Cleaner Create Room Experience
Simplified the room creation modal:

- **Removed 2nd back button**: Just one back button in header
- **Clickable upload boxes**: Picture icon boxes now open file picker
- **Auto-scroll to top**: Each page starts at top (no more mid-page starts)
- **Conditional formatting**: Different layouts for different use cases
- **Removed "Advanced" section**: Cleaner, less overwhelming

### Persona Improvements (Roleplay Users)
Better persona management for roleplay use case:

- **Only shows for roleplay users**: Casual/smart use cases don't see persona UI
- **Top placement**: Persona selector moved to top of room creation
- **Better labels**: "MY NAME" and "MY BACKSTORY" instead of generic labels
- **Helpful hints**: Example placeholders (kpop stan, basketball player, etc.)
- **Full-width cards**: Persona cards span full profile width
- **Scrollable instructions**: Thin viewport for long persona descriptions

---

## 🔍 Search & Discovery

### Room Directory Improvements
Better way to find active rooms:

- **Sort by activity**: Rooms now sorted by most recent message (not upvotes)
- **No pagination**: All featured rooms load at once
- **Fixed timezone**: Timestamps now show "7 hours ago" not "in 7 hours"
- **Removed upvoting**: Cleaner UI, focus on content quality

### Command Palette (Cmd+K) Fixes
Fixed duplicate results and improved search:

- **No duplicates**: Rooms and DMs only appear once
- **Shape communities**: Now included in search results
- **Favorite DMs**: Appear at top of DM list
- **Better deduplication**: Smarter merging of overlapping categories

### In-Room Message Search
Enhanced search with new capabilities:

- **Search by sender**: Use `from:username` to filter messages
- **Submit to search**: Click Enter button to run search (no auto-search)
- **Better performance**: Searches only run when you click submit
- **Clear state**: Proper reset between searches

---

## 🎖️ Badges & Levels

### Cleaner Badge Display
Improved badge system for less clutter:

- **In chat**: Only show your highest-priority badge (team > sponsor > room > level)
- **In profile modal**: Show all your badges
- **Your own messages**: Now show your badges too
- **Clickable**: Click badges to view badge details

### Premium Badge
- New "Premium" badge for subscribers
- Shows in chat and profile modal
- Removed badge preferences UI (no longer needed with 1-badge display)

---

## 🔧 Settings & Configuration

### Settings Menu Reorganization
Moved settings for better discoverability:

- **Private Account toggle**: Now in Settings popup (not sidebar dropdown)
- **Better organization**: All privacy settings in one place

### UI Settings
New appearance customization options:

- **Bubble style selector**: Choose your message bubble shape
- **Effect selector**: Pick your default message effect
- **Effects off mode**: Disable all automatic effects

---

## 🛡️ Moderation & Safety

### User Search by UID
Moderation system now supports searching by user ID:

- **Three search modes**: Email | Username | UID
- **Use case**: Find users when email/username unknown
- **Rooms tab**: Search user's chat history by UID
- **Users tab**: Search users for banning/moderation

### Banned User Improvements
Better handling of banned/deleted users:

- **Deleted variant**: Modal shows when user is deleted (not just banned)
- **Message filtering**: Globally banned user messages now hidden
- **Cleaner UI**: Proper state indication

### Moderation UI Polish
- **Deleted badge**: Shows "Deleted" badge on moderation UI
- **Super editorial access**: Staff can view deleted rooms for moderation
- **Better context**: More info when handling moderation cases

---

## 🎮 User Experience Polish

### Mobile Improvements
Better mobile chat experience:

- **Hidden emoji button**: Saves screen space (keyboard has emoji)
- **Fixed focus issues**: Emoji picker doesn't steal input focus
- **Better voice UX**: Loading states, no double-sends

### Light Mode Fixes
Fixed visibility issues in light mode:

- **Link colors**: Links now visible in "no bubble" style
- **Proper contrast**: Blue (#2563eb) in light, lighter blue (#60a5fa) in dark
- **Hover states**: Better visual feedback

### Forum/Directory Polish
Cleaner community pages:

- **Fixed bleeding**: Long titles/descriptions wrap properly
- **Tappable cards**: Whole card clickable (except controls)
- **Upvote moved**: Now below description, cleaner layout
- **Mobile sidebar**: Square trigger button on mobile

---

## ⚙️ Technical Improvements

### Session Management
Fixed unexpected logouts:

- **100-day idle**: Can be inactive for 100 days and stay logged in
- **1-year absolute**: Sessions last up to 1 year for active users
- **Auto-refresh**: Sessions refresh on any visit
- **Effectively**: "Stay logged in forever" for active users

### SSE & Typing Indicators
Better real-time experience:

- **Extended timeout**: Typing indicators stay for 60 minutes (was 2 min)
- **Long-running tasks**: Shapes can work longer without timeout
- **Better reliability**: Fewer false "stopped typing" indicators

### Performance Optimizations
- **Voice status batching**: Reduced N+1 queries for voice message status
- **Shape info caching**: Fetched on layout for better performance
- **User engagement tracking**: Bulk tracking for analytics

### Notification Improvements
- **Suppressed errors**: Notification endpoint errors no longer show to users
- **Server-side logging**: Errors logged for debugging only
- **Cleaner UX**: No more unexpected error toasts

---

## 🗑️ Removed Features

### Starter Suggestions (Reverted)
- Removed the 3-suggestion bubbles in new rooms
- **Why**: Too spammy, low usage, cluttered UX
- **Cleaned up**: Removed all related code

### Shape Reply Style Toggle (Reverted)
- Removed the shape reply style feature
- **Why**: Confusing UX, unclear value
- **Impact**: Shapes always use default reply style now

### Square Labs
- Removed unused Square Labs feature
- Code cleanup

---

## 📅 Date-by-Date Summary

**October 20:**
- Video call camera toggle fixes
- Room cloning for owners
- Alive mode auto-nudge
- Message polish (timestamps, scroll button)

**October 18:**
- TikTok link previews
- Profile gradient rewards
- Bubble style "Effects off" option
- Onboarding redirect fixes

**October 17:**
- Major rewards system launch (bubbles, effects, gradients)
- Skill instruction editing
- Room branding fixes
- Badge system improvements

**October 16:**
- Auto-collapse long messages
- Message action menu improvements
- Custom instructions UX overhaul
- Settings menu reorganization

**October 15:**
- Command palette deduplication
- Message search by sender
- Persona UI improvements

**October 14:**
- Room directory activity sorting
- Persona visibility (roleplay only)
- Moderation improvements

**October 12-13:**
- Session duration fixes
- Moderation UID search
- Voice message fixes
- Forum UI polish

**October 9-11:**
- Badge system overhaul
- Private account setting moved
- Slash command improvements
- SSE timeout extensions

**October 3-8:**
- Various bug fixes
- Performance optimizations
- Code cleanup