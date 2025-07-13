# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Neovim configuration based on kickstart.nvim - a single-file, well-documented starting point for Neovim. The configuration is intentionally kept in a single `init.lua` file for clarity and educational purposes.

## Common Commands

### Plugin Management
- `:Lazy` - Open Lazy plugin manager UI
- `:Lazy sync` - Update all plugins
- `:Lazy restore` - Restore plugins to versions in lazy-lock.json

### LSP and Mason Commands
- `:Mason` - Open Mason UI to install/manage language servers
- `:LspInfo` - Show active LSP clients for current buffer
- `:LspInstall [server]` - Install a language server via Mason

### Formatting and Linting
- Format current buffer: `<leader>f` (runs conform.nvim formatter)
- The configuration uses:
  - `conform.nvim` for code formatting (configured with stylua for Lua files)
  - `nvim-lint` for linting (configured with markdownlint for Markdown files)

### Key Navigation Patterns
- Leader key: `<space>`
- Search files: `<leader>sf` (Telescope find files)
- Search by grep: `<leader>sg` (Telescope live grep)
- Recent files: `<leader>s.` (Telescope oldfiles)
- LSP actions use `gr` prefix (e.g., `grr` for references, `grn` for rename)

## Architecture

### Configuration Structure
The entire configuration lives in `init.lua` with these main sections:
1. **Leader setup and basic options** - Core Vim settings
2. **Keymaps** - Basic navigation and window management
3. **Plugin installation** - Lazy.nvim bootstrap and plugin specs
4. **Plugin configurations** - Inline configuration for each plugin

### Plugin System
- **Manager**: lazy.nvim (auto-installs if missing)
- **Lock file**: `lazy-lock.json` tracks exact versions
- **Optional plugins**: Located in `lua/kickstart/plugins/` (can be uncommented in init.lua)
- **Custom plugins**: Add to `lua/custom/plugins/` directory

### Key Plugins
- **Completion**: blink.cmp (recently switched from nvim-cmp)
- **LSP**: nvim-lspconfig + Mason for automatic server installation
- **Fuzzy finding**: Telescope with fzf-native
- **Syntax**: Treesitter for highlighting and text objects
- **Git**: Gitsigns for git integration
- **UI**: which-key for keymap discovery, tokyonight colorscheme

### Development Patterns
- Single-file configuration approach - everything in init.lua
- Extensive inline documentation explaining each section
- Modular plugin specifications using lazy.nvim's format
- Conditional features (e.g., Nerd Font support via `vim.g.have_nerd_font`)
- No build system needed - this is configuration, not compiled code

## Important Notes
- This is NOT a Neovim distribution - it's a starting point meant to be understood and modified
- All changes should maintain the single-file philosophy unless splitting is intentional
- When adding plugins, follow the existing inline specification pattern
- Keybindings should use `<leader>` prefix for consistency