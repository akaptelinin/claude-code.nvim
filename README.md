# Claude Code Neovim Plugin

Fork of [coder/claudecode.nvim](https://github.com/coder/claudecode.nvim) with features from [greggh/claude-code.nvim](https://github.com/greggh/claude-code.nvim).

## Changes from upstream

- Removed diff/open_diff functionality (Claude Code shows diffs in terminal instead)
- Removed ClaudeCodeDiffAccept/ClaudeCodeDiffDeny commands
- Removed diff_opts configuration
- Added horizontal split support (top/bottom)
- Added snacks.nvim picker support
- ClaudeCodeSend now falls back to adding current file when no selection
- Added terminal keymaps: `<C-h/j/k/l>` for window navigation, `<C-f/b>` for scrolling
- Auto-insert mode when focusing terminal window

## Features (from upstream)

- WebSocket MCP server for Claude Code CLI integration
- Send current buffer, visual selection, or tree files to Claude context
- Native terminal integration
- Selection tracking

## Supported file explorers

- neo-tree
- nvim-tree
- oil.nvim
- mini.files
- netrw
- snacks.nvim picker

## Commands

| Command | Description |
|---------|-------------|
| `:ClaudeCode` | Toggle Claude terminal |
| `:ClaudeCodeSend` | Send selection (visual) or add current file (normal) |
| `:ClaudeCodeTreeAdd` | Add file from tree explorer |
| `:ClaudeCodeAdd <file> [start] [end]` | Add file with optional line range |

## Installation

```lua
-- lazy.nvim
{
  dir = "~/git/claude-code.nvim",
  dependencies = { "nvim-lua/plenary.nvim" },
  opts = {
    terminal_cmd = "claude",
    terminal = {
      split_side = "bottom", -- "left", "right", "top", "bottom"
      split_width_percentage = 0.5,
      provider = "native",
    },
  },
  keys = {
    { "<leader>ac", "<cmd>ClaudeCode<cr>", desc = "Toggle Claude" },
    { "<C-,>", "<cmd>ClaudeCode<cr>", mode = { "n", "t" } },
    { "<leader>as", "<cmd>ClaudeCodeSend<cr>", mode = "n", desc = "Add file to Claude" },
    { "<leader>as", ":<C-u>ClaudeCodeSend<cr>", mode = "v", desc = "Send selection to Claude" },
  },
}
```

## Configuration

See [coder/claudecode.nvim](https://github.com/coder/claudecode.nvim) for full configuration options (except diff_opts which is removed).
