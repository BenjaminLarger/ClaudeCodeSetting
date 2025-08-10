# Claude Code Audio Hooks Setup

This setup provides audio notifications for all Claude Code hook events with overlap prevention.

## 🎵 Audio Files

Audio files are located in `/home/blarger/.claude/mp3_voices/`:

### Basic Hook Events
- `UserPromptSubmit.mp3` - When you submit a prompt
- `Stop.mp3` - When Claude finishes responding
- `SubagentStop.mp3` - When Task tool completes
- `Notification.mp3` - Permission requests or 60s idle
- `PreCompact.mp3` - Before memory compaction

### Tool-Specific Audio (PreToolUse)
- `PreToolUse-Write.wav.mp3` - Before Write operations
- `PreToolUse-Read.wav.mp3` - Before Read operations
- `PreToolUse-Edit.wav.mp3` - Before Edit operations
- `PreToolUse-Bash.wav.mp3` - Before Bash commands
- `PreToolUse-Task.wav.mp3` - Before Task tool
- `PreToolUse-WebFetch.mp3` - Before WebFetch operations
- `PreToolUse.mp3` - Default for other tools

### Tool-Specific Audio (PostToolUse)
- `PostToolUse-Write.mp3` - After Write operations
- `PostToolUse-Read.mp3` - After Read operations
- `PostToolUse-Edit.mp3` - After Edit operations
- `PostToolUse-Bash.mp3` - After Bash commands
- `PostToolUse-Task.mp3` - After Task tool
- `PostToolUse-WebFetch.mp3` - After WebFetch operations
- `PostToolUse.mp3` - Default for other tools

### Session Events
- `SessionStart-startup.mp3` - New session start
- `SessionStart-resume.mp3` - Resuming session
- `SessionStart-clear.mp3` - After clearing session

## 🔧 Configuration Files

### `settings.json`
Main configuration file at `/home/blarger/.claude/settings.json` contains hook definitions with tool-specific matchers.

### `play_audio.sh`
Audio helper script at `/home/blarger/.claude/play_audio.sh` prevents audio overlap by killing existing audio processes before playing new ones.

## 📋 Commands

### Testing Audio
```bash
# Test individual audio file
./play_audio.sh /home/blarger/.claude/mp3_voices/Stop.mp3

# Run comprehensive hook tests
./test_hooks.sh
```

### Managing Audio
```bash
# Kill all audio processes manually
pkill -f "play.*\.mp3"
pkill -f "ffplay.*\.mp3"

# Check if audio processes are running
ps aux | grep -E "(play|ffplay).*\.mp3"
```

### Hook Testing Script
```bash
# Located at /home/blarger/.claude/test_hooks.sh
chmod +x test_hooks.sh
./test_hooks.sh
```

## 🎯 Hook Events Explained

### PreToolUse / PostToolUse
- **When**: Before/after every tool execution
- **Matchers**: Specific tool names (Write, Read, Edit, Bash, Task, WebFetch)
- **Purpose**: Know exactly what operation is happening

### UserPromptSubmit
- **When**: Before Claude processes your input
- **Purpose**: Confirmation that your message was received

### Stop / SubagentStop
- **When**: Claude finishes main response / Task tool completes
- **Purpose**: Know when operations are complete

### Notification
- **When**: Permission requests or 60+ seconds idle
- **Purpose**: Attention-getting notifications

### PreCompact
- **When**: Before memory compaction (context full)
- **Purpose**: Warning before memory cleanup

### SessionStart
- **When**: Session startup/resume/clear
- **Matchers**: "startup", "resume", "clear"
- **Purpose**: Different sounds for different session states

## 🚀 Features

- **✅ No Audio Overlap**: New sounds interrupt old ones
- **✅ Tool-Specific Sounds**: Different audio for each tool type
- **✅ Session Awareness**: Different startup sounds
- **✅ Comprehensive Coverage**: All 8 hook events supported
- **✅ Easy Testing**: Scripts included for verification

## 🛠️ Customization

### Adding New Audio Files
1. Place MP3 files in `/home/blarger/.claude/mp3_voices/`
2. Update `settings.json` with new matcher/command pairs
3. Test with `./play_audio.sh /path/to/new/file.mp3`

### Modifying Behavior
- Edit `play_audio.sh` to change overlap prevention logic
- Modify `settings.json` matchers for different tool targeting
- Add new matchers for additional tools or patterns

## 🔍 Troubleshooting

### Audio Not Playing
1. Check audio files exist: `ls -la /home/blarger/.claude/mp3_voices/`
2. Test audio manually: `play /path/to/audio.mp3`
3. Verify script permissions: `ls -la /home/blarger/.claude/play_audio.sh`
4. Check if Sox is installed: `which play`

### Hooks Not Triggering
1. Verify settings.json syntax: `cat /home/blarger/.claude/settings.json`
2. Check Claude Code version supports hooks
3. Restart Claude Code session

### Multiple Audio Playing
- The `play_audio.sh` script should prevent this
- Manually kill processes: `pkill -f "play.*\.mp3"`