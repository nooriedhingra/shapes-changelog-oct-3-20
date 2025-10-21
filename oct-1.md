# Shapes.inc Changelog - October 1, 2025

## 🎨 New Features

### Read Out Loud
**PR [#1700](https://github.com/shapesinc/shapes-chat/pull/1700)** by @bielmorales  
**PR [#3145](https://github.com/shapesinc/app/pull/3145)** by @bielmorales
- New voice playback feature for chat messages
- Backend endpoint + frontend UI implementation
- 258 backend additions, 363 frontend additions
- **Impact**: Users can now listen to messages with AI-generated voice

### Fanclub Card
**PR [#1490](https://github.com/shapesinc/shapes.inc/pull/1490)** by @hiidhruv
- New fanclub card component for shapes.inc
- 140 additions, 7 deletions
- **Impact**: Visual representation of shape fan communities

### Tools List UI
**PR [#1703](https://github.com/shapesinc/shapes-chat/pull/1703)** by @francip  
**PR [#3146](https://github.com/shapesinc/app/pull/3146)** by @francip
- Display individual tools in provider UI
- 962 frontend additions, 649 backend additions
- **Impact**: Better tool discoverability and transparency

### Chat Participant Badges
**PR [#1704](https://github.com/shapesinc/shapes-chat/pull/1704)** by @bielmorales  
**PR [#3148](https://github.com/shapesinc/app/pull/3148)** by @bielmorales
- Auto-assign participant badges for sponsored rooms
- 104 frontend additions, 69 backend additions
- **Impact**: Visual recognition for sponsored room participants

## 🔧 Improvements

### Tool Evaluator Schema Alignment
**PR [#3150](https://github.com/shapesinc/app/pull/3150)** by @seanulacra
- Synced eval harness with runtime `normalize_tools`
- Record provider validation failures as `tools_schema_rejected:*`
- 1,088 additions, 315 deletions
- **Impact**: Production-grade schema validation, catches more errors

### Better Reply Context
**PR [#1697](https://github.com/shapesinc/shapes-chat/pull/1697)** by @hiidhruv
- Show full target message in reply context instead of just link
- 85 additions, 8 deletions
- **Impact**: More contextual information for shapes responding to replies

### MCP Documentation Link
**PR [#1688](https://github.com/shapesinc/shapes-chat/pull/1688)** by @anushkmittal
- Added MCP docs link under "Shape Skills" in room settings
- 11 additions
- **Impact**: Easier access to MCP setup documentation

### Terminology Standardization
**PR [#1686](https://github.com/shapesinc/shapes-chat/pull/1686)** by @anushkmittal  
**PR [#1692](https://github.com/shapesinc/shapes-chat/pull/1692)** by @anushkmittal  
**PR [#1693](https://github.com/shapesinc/shapes-chat/pull/1693)** by @anushkmittal
- Renamed "tool calls" → "shapes actions" → "skills used"
- Consistent terminology across frontend
- **Impact**: Clearer, more user-friendly language

## 🐛 Bug Fixes

### Voice Transcription Hotfix
**PR [#3149](https://github.com/shapesinc/app/pull/3149)** by @bielmorales
- Fixed NoneType error for voice_transcription_url
- 1 addition, 1 deletion
- **Impact**: Prevents crashes when voice transcription URL is missing

### Shape Interaction Modal Fix
**PR [#1696](https://github.com/shapesinc/shapes-chat/pull/1696)** by @hiidhruv
- Fixed broken shape interaction modal on shape directory
- 33 additions, 14 deletions
- **Impact**: Users can now interact with shapes from directory again

### UI Refinements
**PR [#1699](https://github.com/shapesinc/shapes-chat/pull/1699)** by @nooriedhingra  
**PR [#1701](https://github.com/shapesinc/shapes-chat/pull/1701)** by @loamyx  
**PR [#1694](https://github.com/shapesinc/shapes-chat/pull/1694)** by @hiidhruv  
**PR [#1695](https://github.com/shapesinc/shapes-chat/pull/1695)** by @hiidhruv
- Removed "Open DM" from user hover pills
- Removed Private/Public tags from Chat Now menu
- Increased highlight height for better visibility
- Reinstated previous UI improvements

---

**Total**: 15 merged PRs
- **shapesinc/app**: 5 PRs
- **shapesinc/shapes-chat**: 9 PRs
- **shapesinc/shapes.inc**: 1 PR
