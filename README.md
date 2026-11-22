# Text Editor

A lightweight terminal-based text editor written in C++, inspired by the classic `kilo` editor. Built from scratch using raw terminal I/O with no external dependencies beyond the C++ standard library.

## Features

- **Raw terminal mode** — direct, low-level keyboard and display control
- **File open & save** — open existing files from the command line and save with `Ctrl-S`
- **Full cursor navigation** — arrow keys, Home/End, Page Up/Page Down
- **Text editing** — insert characters, newlines (Enter), backspace, and delete
- **Line operations** — split lines on Enter, merge lines on Backspace at line start
- **Horizontal & vertical scrolling** — handles files wider and longer than the terminal
- **Status bar** — displays filename, line count, and unsaved-changes indicator
- **Message bar** — shows contextual messages and warnings (fades after 5 seconds)
- **Unsaved-change protection** — requires pressing `Ctrl-Q` three times to quit with unsaved changes
- **Tab rendering** — tabs are expanded to the nearest 8-space boundary

## Requirements

- A POSIX-compatible system (Linux, macOS)
- A C++17-capable compiler (e.g. `g++`, `clang++`)

## Building

```bash
g++ -std=c++17 -Wall -Wextra -o editor main.cpp
```

## Usage

```bash
# Open the editor with no file (new file)
./editor

# Open an existing file
./editor <filename>
```

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `Ctrl-S` | Save file |
| `Ctrl-Q` | Quit (press 3× with unsaved changes) |
| `Arrow Keys` | Move cursor |
| `Home` / `End` | Jump to start/end of line |
| `Page Up` / `Page Down` | Scroll one screen at a time |
| `Backspace` / `Ctrl-H` | Delete character to the left |
| `Delete` | Delete character to the right |
| `Enter` | Insert new line |

## Project Structure

The editor is organized into five classes, all in a single `main.cpp` file:

| Class | Responsibility |
|---|---|
| `Terminal` | Raw mode, key reading, window size, screen output |
| `AppendBuffer` | Efficient string building for screen refresh |
| `EditorRow` | Single line of text and its rendered representation |
| `TextBuffer` | Collection of rows, file I/O, and edit operations |
| `Editor` | Top-level coordinator — cursor, scrolling, key handling, UI |

