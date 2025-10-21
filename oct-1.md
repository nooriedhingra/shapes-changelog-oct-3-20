# Shapes.inc Changelog - October 1, 2025

## 🎨 New Features

### Read Out Loud Endpoint
- **PR #3145** by @bielmorales
- New backend endpoint for read-out-loud functionality
- 258 additions, 8 deletions
- **Impact**: Enables voice playback of chat messages

### Chat Participant Badges
- **PR #3148** by @bielmorales 
- Automatic participant badge assignment when room is sponsored
- 69 additions, 2 deletions
- **Impact**: Visual recognition for sponsored room participants

## 🔧 Improvements

### Tool Evaluator Schema Detection
- **PR #3150** by @seanulacra
- Tightened tool evaluator schema validation and detection
- Aligned eval harness with runtime normalize_tools
- 1,088 additions, 315 deletions
- **Impact**: More robust tool calling validation and error catching

## 🐛 Bug Fixes

### Voice Transcription URL Hotfix
- **PR #3149** by @bielmorales
- Fixed NoneType error for voice_transcription_url
- 1 addition, 1 deletion
- **Impact**: Prevents crashes when voice transcription URL is missing

### Tools List (shapesinc/app)
- **PR #3146** by @francip (merged Oct 1 at 22:11:53Z)
- Added information about individual tools
- **Impact**: Better tool discoverability and documentation

### Simple MCP Validation (shapesinc/app)
- **PR #3143** by @seanulacra (merged Oct 1 at 03:12:33Z)
- Hardened simple MCP validation to reject bogus URLs
- Fail validation when MCP server returns zero tools
- **Impact**: Stricter handshake behavior, better error handling

### STM Window Update Script (shapesinc/app)
- **PR #3141** by @francip (merged Oct 1 at 01:46:59Z)
- Mass update STM window script
- **Impact**: Improved STM window management

---

**shapes-chat**: 9 merged PRs
**shapesinc/app**: 7 merged PRs  
**Total Changes**: 16 merged pull requests
