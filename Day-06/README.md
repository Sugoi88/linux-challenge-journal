# Day 06 - Editing with Vim

## Objective

Practice editing text files using `vi` and `vim`, with a focus on understanding Vim's modal editing system and becoming more comfortable with basic navigation and editing commands.

The goal of this lesson was not to master Vim, but to build enough familiarity to confidently use it when working on Linux systems where a simpler editor may not be available.

---

## Topics Covered

- `vi` and `vim`
- Normal mode
- Insert mode
- Basic cursor movement
- Editing text
- Searching within files
- Deleting and restoring text
- Writing changes to disk
- Exiting Vim safely
- Using `vimtutor`
- Basic Vim customization

---

## `vi` and `vim`

`vi` is one of the traditional Unix text editors.

`vim`, or **Vi IMproved**, is a more feature-rich descendant of `vi`.

Depending on the Linux distribution, running:

```bash
vi
```

may actually launch Vim or another compatible implementation.

The installed version can be checked with:

```bash
vi --version
```

or:

```bash
vim --version
```

---

## Installing Vim

If Vim is not already installed on an Ubuntu or Debian-based system, it can be installed with:

```bash
sudo apt install vim
```

Once installed, Vim can be launched with:

```bash
vim filename
```

---

## Vim Modes

One of the most important concepts in Vim is that the editor operates in different modes.

Two primary modes introduced during this lesson were:

- **Normal mode**
- **Insert mode**

---

### Normal Mode

Normal mode is used for commands and navigation.

When Vim first opens a file, it normally begins in this mode.

Pressing:

```text
Esc
```

returns to normal mode.

When unsure which mode Vim is currently in, pressing `Esc` once or twice is a reliable way to return to normal mode.

---

### Insert Mode

Insert mode allows text to be entered normally.

From normal mode, press:

```text
i
```

to enter insert mode.

When finished editing, press:

```text
Esc
```

to return to normal mode.

---

## Opening a File

A file can be opened with:

```bash
vim filename
```

For example:

```bash
vim testfile
```

The challenge used a copy of `/etc/services` for practice:

```bash
cp /etc/services testfile
vim testfile
```

This provides a safe file to experiment with without modifying an important system file.

---

## Basic Navigation

Traditional Vim navigation uses:

```text
h  j  k  l
```

These correspond to:

| Key | Movement |
|---|---|
| `h` | Left |
| `j` | Down |
| `k` | Up |
| `l` | Right |

Arrow keys also work in most modern Vim installations.

The traditional navigation keys are still worth knowing because they are part of the standard Vim workflow.

---

## Navigating Through a File

Move to the beginning of the file:

```text
gg
```

Move to the end of the file:

```text
G
```

These commands are useful when navigating large configuration or log files.

---

## Searching

Search forward through a file with:

```text
/searchterm
```

For example:

```text
/ssh
```

Press:

```text
n
```

to move to the next result.

Press:

```text
N
```

to move to the previous result.

---

## Deleting Text

Delete the current line:

```text
dd
```

A number can be placed before a command to repeat it.

For example:

```text
5dd
```

deletes five lines.

Similarly:

```text
33dd
```

deletes thirty-three lines.

This pattern of combining counts with commands is common throughout Vim.

---

## Undo

Undo the most recent change:

```text
u
```

This is particularly useful while practicing commands that may modify more text than intended.

---

## Copying and Pasting

In Vim terminology, deleting text can also place it into a buffer that can later be pasted.

For example:

```text
5dd
```

deletes five lines.

Press:

```text
P
```

to paste them before the current cursor position.

Vim provides many additional copy and paste commands beyond the basics covered during this lesson.

---

## Editing Text

Enter insert mode:

```text
i
```

Begin typing normally.

When finished:

```text
Esc
```

returns to normal mode.

This distinction between editing text and issuing commands is one of the biggest differences between Vim and editors such as Nano.

---

## Saving Changes

Write changes to disk without leaving Vim:

```text
:w
```

---

## Save and Exit

Save the file and exit Vim:

```text
:wq
```

Another commonly used shortcut is:

```text
ZZ
```

from normal mode.

---

## Exit Without Saving

To discard changes and exit:

```text
:q!
```

This is one of the most important commands to remember when first learning Vim.

When experimentation goes sideways:

```text
Esc
:q!
```

is the emergency exit.

---

## Useful Vim Commands

| Command | Action |
|---|---|
| `i` | Enter insert mode |
| `Esc` | Return to normal mode |
| `h` | Move left |
| `j` | Move down |
| `k` | Move up |
| `l` | Move right |
| `gg` | Go to beginning of file |
| `G` | Go to end of file |
| `/text` | Search |
| `n` | Next search result |
| `N` | Previous search result |
| `dd` | Delete current line |
| `5dd` | Delete five lines |
| `u` | Undo |
| `P` | Paste before cursor |
| `:w` | Save |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

---

## Vim Tutor

Vim includes an interactive tutorial:

```bash
vimtutor
```

The tutorial walks through common commands and editing techniques in a hands-on format.

It is useful for building muscle memory because Vim becomes significantly easier once common navigation and editing commands begin to feel automatic.

---

## Why Learn Vim?

Editors such as Nano are easier to approach because their controls resemble traditional text editors and many shortcuts are displayed directly on screen.

Vim has a steeper learning curve, but there are several reasons why basic familiarity is useful:

- It is commonly available on Linux and Unix systems
- It works entirely from a terminal
- It is useful over SSH
- It does not require a graphical environment
- It is frequently encountered when editing system configuration files
- It can be extremely efficient once the commands become familiar

For Linux administration, the goal does not necessarily need to be becoming a Vim power user.

Being able to confidently open, modify, save, and exit a file is already a useful operational skill.

---

## Vim Configuration

Vim can be customized using:

```text
~/.vimrc
```

Possible configuration options include:

- Syntax highlighting
- Line numbers
- Indentation behavior
- Search behavior
- Tab settings
- Custom key mappings

For example:

```vim
set number
syntax on
```

would enable line numbers and syntax highlighting.

Customization can make Vim more comfortable for regular use.

---

## Key Takeaways

The biggest difference between Vim and simpler editors is its modal design.

The most important pattern to remember is:

```text
Normal Mode -> Command
Insert Mode -> Text Entry
```

When uncertain:

```text
Esc
```

returns to normal mode.

From there, several essential commands are enough to perform basic editing:

```text
i
:w
:wq
:q!
dd
u
/
```

Knowing these basics makes it possible to work with configuration and text files on systems where another editor may not be available.

---

## Personal Notes

Day 06 was a straightforward review of `vi` and `vim`.

I already have some familiarity with both Vim and Nano and do not have a strong preference against either one.

I tend to switch between them depending on the task and what I am working on.

For quick configuration changes or simple text edits, I am perfectly comfortable using:

```bash
nano
```

For other tasks, especially when working on systems where Vim is readily available or when I want more powerful navigation and editing controls, I am also comfortable using:

```bash
vim
```

or:

```bash
vi
```

I see value in being familiar with both rather than treating editor choice as an either-or decision.

Nano offers simplicity and immediate usability, while Vim provides a much deeper command-driven editing workflow once its controls become familiar.

For Linux administration, flexibility is more useful to me than loyalty to a particular editor.

---

## Status

✅ Day 06 Completed
