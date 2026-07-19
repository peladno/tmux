# 🧩 Tmux Configuration

This repository contains my personal tmux configuration, designed for a Vim-centric workflow, productivity, and a clean modern interface using the Catppuccin theme. It is optimized for daily development work and integrates seamlessly with Neovim.

---

## ✨ Features

- Prefix key set to `Ctrl + a`
- Vim-style pane navigation and resizing
- Mouse support enabled
- True color (24-bit) terminal support
- Persistent tmux sessions across reboots
- Fast session switching
- Clean and informative status bar
- Plugin management via TPM

---

## ⌨️ Key Bindings

### Prefix

- `Ctrl + a`

### Reload configuration

- `Prefix + r` — reload `~/.config/tmux/tmux.conf`

### Pane splits

- `Prefix + |` — split pane horizontally (`split-window -h`)
- `Prefix + -` — split pane vertically (`split-window -v`)

All new panes open in the current pane directory.

### Pane resizing (Vim style)

- `Prefix + h` — resize pane left
- `Prefix + j` — resize pane down
- `Prefix + k` — resize pane up
- `Prefix + l` — resize pane right

### Maximize / restore pane

- `Prefix + m` — toggle pane zoom (`resize-pane -Z`)

### Copy mode (Vi keys)

- `Prefix + v` — enter copy mode
- `v` — begin selection
- `y` — copy selection

Mouse selection in copy mode is disabled to avoid conflicts.

### Window management

- `Prefix + c` — create a new window (default tmux binding)
- `Prefix + ,` — rename current window (default tmux binding)
- `Prefix + &` — kill current window (default tmux binding)
- `Prefix + p` — previous window (default tmux binding)
- `Prefix + <number>` — select window by number (default tmux binding)
- `Alt + h` — move current window left (`move-window -r`)

### Session management

- `Prefix + n` — create a new named session
- `Prefix + I` — install plugins with TPM
- `Prefix + U` — update plugins with TPM
- `Prefix + Alt + u` — remove unused plugins with TPM

---

## 🖱️ Mouse and terminal

- `mouse on` — mouse support enabled
- `tmux-256color` — default terminal
- RGB passthrough enabled for true color

---

## 🔌 Plugins

Plugins are managed with **Tmux Plugin Manager (TPM)**.

### Installed plugins

#### tmux-plugins/tpm

Plugin manager for tmux.

Commands:

- `Prefix + I` — install plugins
- `Prefix + U` — update plugins
- `Prefix + Alt + u` — remove unused plugins

---

#### christoomey/vim-tmux-navigator

Seamless navigation between tmux panes and Neovim splits.

Commands:

- `Ctrl + h` / `Ctrl + j` / `Ctrl + k` / `Ctrl + l` — move between tmux panes and Neovim splits

---

#### omerxx/tmux-sessionx

Interactive tmux session manager.

Commands:

- `Prefix + o` — open session switcher

---

#### tmux-plugins/tmux-continuum

Automatic session saving and restoring.

Behavior:

- Automatically saves sessions every 15 minutes
- Automatically restores sessions at tmux startup
- No extra manual commands required

---

#### catppuccin/tmux

Catppuccin theme for tmux.

Behavior:

- Applies the `mocha` flavor
- Styles the status bar and window/pane appearance
- No runtime commands required

---

#### tmux-plugins/tmux-online-status

Shows network connectivity status in the status bar.

Behavior:

- Displays `on` or `off` automatically
- No runtime commands required

---

#### tmux-plugins/tmux-battery

Displays battery status in the status bar.

Behavior:

- Shows battery icon and percentage automatically
- No runtime commands required

---

## 🎨 Theme and Status Bar

- Theme: Catppuccin Mocha
- Minimal pane borders
- Clean window list
- Status bar displays:
  - Session name
  - Current working directory
  - Zoom indicator
  - Battery percentage
  - Online / offline status

The status bar is positioned at the bottom and centered.

---

## 🔄 Session Persistence

- Sessions are automatically saved every 15 minutes
- Sessions are restored automatically on tmux startup
- Pane contents are preserved

---

## 📁 Plugin Path

Plugins are stored in:
~/.config/tmux/plugins

---

## 🚀 Installation

1. Clone TPM:
   git clone https://github.com/tmux-plugins/tpm ~/.config/tmux/plugins/tpm

2. Start tmux and install plugins:
   `Prefix + I`

3. Reload configuration:
   `Prefix + r`

---

## 📝 Notes

This configuration is designed for keyboard-driven workflows, optimized for Neovim users, and focused on being clean, minimal, and fast.
