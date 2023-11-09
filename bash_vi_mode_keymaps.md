
# Bash VI Mode Keymaps

## Introduction

This document lists key mappings for Bash when VI mode is enabled. In VI mode, Bash allows you to navigate and edit your command line with VI-like controls.

To enable VI mode in Bash, run:
\`\`\`
set -o vi
\`\`\`

## Modes

In VI mode, you have two primary modes:

- **Normal Mode**: Navigate and manipulate text.
- **Insert Mode**: Insert text.

---

## Normal Mode

| Key       | Action                               |
|-----------|--------------------------------------|
| `Esc`     | Enter Normal Mode                    |
| `0`       | Move to the beginning of the line    |
| `$`       | Move to the end of the line          |
| `w`       | Move forward one word                |
| `b`       | Move backward one word               |
| `dd`      | Delete the entire line               |
| `D`       | Delete from cursor to end of line    |
| `u`       | Undo the last change                 |
| `Ctrl`+`r`| Redo the last undo                   |

---

## Insert Mode

| Key       | Action                     |
|-----------|----------------------------|
| `i`       | Enter Insert Mode          |
| `I`       | Insert at the beginning    |
| `a`       | Append after the cursor    |
| `A`       | Append at the end          |
| `o`       | Open a new line below      |
| `O`       | Open a new line above      |

---

To switch between modes, use `Esc` to go to Normal Mode and `i` to go back to Insert Mode.

