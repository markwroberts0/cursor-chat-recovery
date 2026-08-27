# 🔄 Cursor Chat Recovery

A CLI tool to recover conversations, plans, and chat history from [Cursor](https://cursor.com)'s local database.

Ever lost a chat or plan in Cursor? This tool lets you browse and export all your conversation history directly from Cursor's SQLite database.

![Demo](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux%20%7C%20Windows-blue)
![Python](https://img.shields.io/badge/Python-3.7+-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## ✨ Features

- 📋 **List all conversations** — Browse your entire chat history
- 🔍 **View conversations** — Preview or view full conversation with tool calls
- 📤 **Export to Markdown** — Save conversations as formatted `.md` files
- 📦 **Export all at once** — Bulk-export every conversation to a folder in one go
- 📝 **Extract plans** — Pull out Plan Mode plans with to-do lists
- 🔧 **Tool call support** — See all AI tool calls (file edits, terminal commands, etc.)
- 🎨 **Beautiful CLI** — Clean, colorful terminal interface

## 📦 Installation

### Quick Install

```bash
# Clone the repo
git clone https://github.com/yourusername/cursor-chat-recovery.git
cd cursor-chat-recovery

# Make executable
chmod +x cursor-recover

# Run it
./cursor-recover
```

### Install Globally (optional)

```bash
# Symlink to your PATH
sudo ln -sf "$(pwd)/cursor-recover" /usr/local/bin/cursor-recover

# Now run from anywhere
cursor-recover
```

## 🚀 Usage

```bash
./cursor-recover
```

You'll see an interactive menu:

```
╔══════════════════════════════════════════════════════════════╗
║              🔄 Cursor Chat Recovery CLI v1.0.0               ║
╚══════════════════════════════════════════════════════════════╝

Found 11 conversations:

    1  Lost Cursor chats and plans                      │ 166 msgs │ 2026-01-05 11:41
    2  Automated home inventory system                  │  54 msgs │ 2026-01-05 11:30
    3  Create a Jarvis-like voice agent                 │  85 msgs │ 2025-08-16 14:01
    ...

Enter number to select, q to quit
```

### Actions

Once you select a conversation:

1. **View full conversation** — See all messages with tool calls
2. **Export to Markdown** — Save as a formatted `.md` file
3. **Extract plan** — If the conversation has a Plan Mode plan, extract it
4. **Back to list** — Return to conversation list

Or from the conversation list, press **`e`** to **Export All**:

- You'll be prompted for an output folder (defaults to `./recovered/` next to the script)
- Every conversation is exported as a numbered, named `.md` file: `01_My_Project.md`, `02_Another_Chat.md`, …
- Live progress is shown for each conversation

## 📁 What Gets Recovered

- **Chat messages** — Both user and AI messages
- **Tool calls** — File edits, terminal commands, plans, questions
- **Plans** — Full Plan Mode plans with to-dos
- **Timestamps** — When each message was created

## 🗂️ Database Locations

The tool automatically finds Cursor's database:

| Platform | Path |
|----------|------|
| **macOS** | `~/Library/Application Support/Cursor/User/globalStorage/state.vscdb` |
| **Linux** | `~/.config/Cursor/User/globalStorage/state.vscdb` |
| **Windows** | `%APPDATA%/Cursor/User/globalStorage/state.vscdb` |

## 📋 Requirements

- Python 3.7+
- No external dependencies (uses only standard library)

## 🔧 How It Works

Cursor stores conversation data in a SQLite database (`state.vscdb`). This tool:

1. Connects to the database (read-only)
2. Extracts `composerData` entries (conversation metadata)
3. Extracts `bubbleId` entries (message content and tool calls)
4. Formats and displays/exports the data

**Note:** This tool only reads data — it never modifies your Cursor database.

## 🤔 FAQ

### Why can't I see some messages?

Some AI messages only contain tool calls (like file edits) without visible text. The tool shows these as tool call blocks.

### Can I recover deleted conversations?

Only if Cursor hasn't overwritten the data. Try the backup database option — Cursor maintains a `.backup` file.

### Does this work with VS Code?

No, this is specifically for [Cursor](https://cursor.com). VS Code has a different data structure.

## 🤝 Contributing

Contributions welcome! Feel free to:

- Report bugs
- Suggest features
- Submit pull requests

## 📜 License

MIT License — see [LICENSE](LICENSE) file.

## 🙏 Acknowledgments

Inspired by [CursorRecovery](https://github.com/bbostock/CursorRecovery) — this is a streamlined CLI-only version with updated database parsing.

