# 🧩 Tmux Configuration

This repository contains my personal tmux configuration, designed for a Vim‑centric workflow, productivity, and a clean modern interface using the Catppuccin theme. It is optimized for daily development work and integrates seamlessly with Neovim.

---

## ✨ Features

- Prefix key set to Ctrl + a
- Vim‑style pane navigation and resizing
- Mouse support enabled
- True color (24‑bit) terminal support
- Persistent tmux sessions across reboots
- Fast session switching
- Clean and informative status bar
- Plugin management via TPM

---

## ⌨️ Key Bindings

### Prefix
Ctrl + a

### Reload tmux configuration
Prefix + r

---

### Pane Splits

- Horizontal split: Prefix + |
- Vertical split: Prefix + -

Splits open in the current pane directory.

---

### Pane Resizing (Vim style)

Resize panes using:
Prefix + h / j / k / l

Maximize or restore pane:
Prefix + m

---

### Copy Mode (Vim bindings)

- Enter copy mode: Prefix + v
- Start selection: v
- Copy selection: y

Mouse drag copy is disabled to avoid conflicts.

---

### Window and Session Management

- Move window left: Alt + h
- Create a new named session: Prefix + n

---

## 🖱️ Mouse and Terminal Support

- Mouse support enabled
- True color support using tmux-256color
- RGB passthrough enabled for modern terminals

---

## 🔌 Plugins

Plugins are managed using **Tmux Plugin Manager (TPM)**.

### Installed Plugins and Commands

#### tmux-plugins/tpm
Tmux Plugin Manager.

Commands:
- Install plugins: Prefix + I
- Update plugins: Prefix + U
- Remove unused plugins: Prefix + Alt + u

---

#### christoomey/vim-tmux-navigator
Seamless navigation between tmux panes and Neovim splits.

Commands:
- Ctrl + h / j / k / l  
  Move between tmux panes and Neovim splits seamlessly.

---

#### omerxx/tmux-sessionx
Fast and interactive tmux session manager.

Commands:
- Prefix + o  
  Open session switcher (fzf-based).

---

#### tmux-plugins/tmux-resurrect
Persist tmux sessions after reboot.

Commands:
- Prefix + Ctrl + s  
  Save tmux session.
- Prefix + Ctrl + r  
  Restore tmux session.

Pane contents are captured automatically.

---

#### tmux-plugins/tmux-continuum
Automatic tmux session saving and restoring.

Behavior:
- Automatically saves sessions every 15 minutes.
- Automatically restores sessions on tmux startup.

No manual commands required.

---

#### catppuccin/tmux
Catppuccin theme for tmux.

Behavior:
- Applies Catppuccin Mocha theme.
- Controls colors for status bar, windows, and panes.

No runtime commands.

---

#### tmux-plugins/tmux-online-status
Displays network connectivity status in the status bar.

Behavior:
- Shows online or offline indicator automatically.

No runtime commands.

---

#### tmux-plugins/tmux-battery
Displays battery status in the status bar.

Behavior:
- Shows battery icon and percentage automatically.

No runtime commands.

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
Prefix + I

3. Reload configuration:
Prefix + r

---

## 📝 Notes

This configuration is designed for keyboard‑driven workflows, optimized for Neovim users, and focused on being clean, minimal, and fast.
🇼🇫
