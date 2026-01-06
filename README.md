# Claude Code Neovim Plugin

Fork of [coder/claudecode.nvim](https://github.com/coder/claudecode.nvim) with diff feature removed.

## Changes from upstream

- Removed diff/open_diff functionality (Claude Code shows diffs in terminal instead)
- Removed ClaudeCodeDiffAccept/ClaudeCodeDiffDeny commands
- Removed diff_opts configuration

## Features (from upstream)

- WebSocket MCP server for Claude Code CLI integration
- Send current buffer, visual selection, or tree files to Claude context
- Native terminal integration
- Selection tracking

## Commands

| Command | Description |
|---------|-------------|
| `:ClaudeCode` | Toggle Claude terminal |
| `:ClaudeCodeSend` | Send visual selection to Claude context |
| `:ClaudeCodeTreeAdd` | Add file from neo-tree/nvim-tree/oil/netrw |
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
      split_side = "right",
      split_width_percentage = 0.5,
      provider = "native",
    },
  },
  keys = {
    { "<leader>ac", "<cmd>ClaudeCode<cr>", desc = "Toggle Claude" },
    { "<C-,>", "<cmd>ClaudeCode<cr>", mode = { "n", "t" } },
    { "<leader>as", ":<C-u>ClaudeCodeSend<cr>", mode = "v" },
    { "<leader>as", "<cmd>ClaudeCodeTreeAdd<cr>", ft = { "neo-tree", "NvimTree", "oil" } },
  },
}
```

## Configuration

See [coder/claudecode.nvim](https://github.com/coder/claudecode.nvim) for full configuration options (except diff_opts which is removed).
