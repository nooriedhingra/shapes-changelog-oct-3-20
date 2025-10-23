## Changelog - October 2, 2025

### New Features

**Training from chat**
Shape creators can now create training data directly from chat conversations. Select messages to convert them into training pairs, making it easier to refine shape behavior based on real interactions.

**AI-generated profile images**
Users and shape creators can now generate profile pictures and banners using AI. Access this feature via the "Generate with AI" option in the profile editor and shape creation wizard.

**Room directory pitch**
Room creators can now add a dedicated "Why join" pitch when submitting rooms to the directory. This promotional text appears on directory cards separately from the room description.

### Improvements

**Room-specific shape settings**
Room creators can now customize shape instructions at the room-shape level. Configure these settings via the "Configure shapes" option in room settings.

**Custom MCP authorization**
Custom MCPs now support authorization headers, enabling authenticated requests. This applies to both API keys and Bearer token authentication.

**Composer autofocus on keyboard activity**
Typing anywhere in the chat now automatically focuses the message composer on desktop. Video and audio embeds continue to work normally without interference.

**Room creation redirect**
After creating a room, the room list now refreshes before redirecting to ensure the new room appears in the sidebar immediately.

### Fixes

**Chat reconnection after sleep**
Fixed chat history becoming stale after laptop sleep or network disconnection. The app now detects connection health and backfills missed messages within the last 30 minutes when reconnecting.

**Onboarding modal state**
Fixed session values not updating properly during onboarding, which caused the onboarding modal to get stuck after room creation.

**Onboarding flow reverted**
The new 3-step onboarding flow (use case selection, shape discovery, profile completion) was temporarily reverted due to issues. The original profile completion modal is back in use.

---

**Summary:** 3 new features, 4 improvements, 3 fixes