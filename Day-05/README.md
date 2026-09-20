# Day 05 - More or Less

## Objective

Review several command-line features that make working in a Linux shell faster and more efficient.

This lesson focused on viewing text files, using command and filename completion, navigating command history, inspecting hidden configuration files, and making small customizations to the shell environment.

---

## Topics Covered

- Viewing files with `more` and `less`
- Navigating and searching inside `less`
- Tab completion
- Bash command history
- Reverse history search
- Re-running previous commands
- Hidden files and dotfiles
- Reviewing `.bashrc` and `.bash_history`
- Basic shell prompt customization
- Editing files with `nano`
- Exploring alternative shells
- Testing terminal multiplexers such as `screen` and `tmux`

---

## Viewing Files

Two common tools for reading text files from the terminal are:

```bash
more filename
less filename
```

Both allow large files to be viewed one screen at a time rather than printing the entire file directly into the terminal.

---

## `more`

Example:

```bash
more /etc/services
```

`more` provides basic paginated viewing of a text file.

It is useful for quickly reading through files that contain more content than can fit on one terminal screen.

---

## `less`

Example:

```bash
less /etc/services
```

Despite the name, `less` generally provides more functionality than `more`.

Some useful controls include:

| Key | Action |
|---|---|
| `Space` | Move forward one screen |
| `b` | Move backward one screen |
| `g` | Go to the beginning of the file |
| `G` | Go to the end of the file |
| `/text` | Search forward for text |
| `n` | Move to the next search result |
| `N` | Move to the previous search result |
| `q` | Quit |

Example search from inside `less`:

```text
/ssh
```

This searches the current file for occurrences of `ssh`.

---

## Tab Completion

The shell can automatically complete commands, filenames, and directory paths using the `Tab` key.

For example:

```bash
les<Tab>
```

may expand to:

```bash
less
```

Tab completion also works with file paths:

```bash
less /etc/serv<Tab>
```

may complete to:

```bash
less /etc/services
```

If more than one match exists, pressing `Tab` again can display the possible options.

For example:

```bash
less /etc/s<Tab><Tab>
```

Tab completion helps:

- Reduce typing
- Avoid spelling mistakes
- Discover available files and commands
- Navigate long directory paths more efficiently

---

## Command History

Bash keeps a history of previously executed commands.

View the history with:

```bash
history
```

The output contains numbered commands from previous shell activity.

Example:

```text
18  ls -la
19  cd /etc
20  less /etc/services
21  history
```

---

## Re-running Commands by History Number

A command can be executed again using its history number.

For example:

```bash
!20
```

This runs command number `20` from the history list.

This can be especially convenient when returning to long or complicated commands.

---

## Navigating History

The `Up Arrow` and `Down Arrow` keys can cycle through previously executed commands.

This makes it easy to:

- Repeat a command
- Modify a previous command
- Correct a typo
- Re-run a command with different arguments

---

## Reverse History Search

One of the most useful Bash shortcuts is:

```text
Ctrl + r
```

After pressing `Ctrl + r`, begin typing part of a previously executed command.

For example:

```text
(reverse-i-search)`ssh':
```

Bash searches the command history and displays a matching previous command.

Pressing `Ctrl + r` again cycles through additional matches.

The result can then either be executed or edited before running.

---

## Hidden Files and Dotfiles

Linux traditionally treats filenames beginning with a period as hidden.

For example:

```text
.bashrc
.bash_history
.profile
.ssh
```

A normal directory listing:

```bash
ls -l
```

does not show most hidden files.

To include them:

```bash
ls -la
```

or:

```bash
ls -ltra
```

Dotfiles are commonly used to store user-specific configuration.

---

## `.bashrc`

A common Bash configuration file is:

```text
~/.bashrc
```

It can be viewed using:

```bash
less ~/.bashrc
```

The file can contain things such as:

- Aliases
- Environment variables
- Shell functions
- Prompt configuration
- Bash behavior settings

Changes to `.bashrc` affect the user's interactive Bash environment.

---

## `.bash_history`

Bash command history is commonly stored in:

```text
~/.bash_history
```

It can be reviewed with:

```bash
less ~/.bash_history
```

This file provides a persistent record of many commands executed during previous Bash sessions.

Because command history can contain sensitive information, passwords, API keys, tokens, and other secrets should never be entered directly into commands when avoidable.

---

## Shell Prompt Customization

The Bash prompt is commonly controlled through the `PS1` environment variable.

View the current prompt configuration:

```bash
echo "$PS1"
```

A temporary prompt can be tested with:

```bash
PS1="\u@\h:\w\$ "
```

Common prompt escape sequences include:

| Sequence | Meaning |
|---|---|
| `\u` | Username |
| `\h` | Hostname |
| `\w` | Current working directory |
| `\t` | Current time |
| `\$` | `$` for normal users or `#` for root |

Changes made directly to `PS1` normally last only for the current shell session.

Persistent customization can be placed in:

```text
~/.bashrc
```

---

## Editing with Nano

The lesson also used the `nano` text editor.

Create or edit a file with:

```bash
nano filename
```

For example:

```bash
nano day-05-summary.txt
```

Some useful shortcuts include:

| Shortcut | Action |
|---|---|
| `Ctrl + O` | Save |
| `Ctrl + X` | Exit |
| `Ctrl + W` | Search |
| `Ctrl + K` | Cut line |
| `Ctrl + U` | Paste |

Nano provides a relatively simple terminal-based editor and displays many common keyboard shortcuts directly at the bottom of the screen.

---

## Five-Day Review

Day 05 also provided an opportunity to reflect on the first portion of the Linux Upskill Challenge.

### Day 01

- SSH access
- System information
- Hardware information
- Resource monitoring
- Networking basics

### Day 02

- Filesystem navigation
- File and directory manipulation
- Linux documentation
- `pushd` and `popd`

### Day 03

- Linux privileges
- `sudo`
- Root access
- Login history
- Hostname and timezone management

### Day 04

- APT package management
- Linux filesystem hierarchy
- Configuration files
- System logs
- Midnight Commander

### Day 05

- Text file viewing
- Tab completion
- Command history
- Dotfiles
- Shell customization
- Terminal multiplexers
- Alternative shells

---

## Extension Topics

The Linux shell environment is highly customizable.

Alternative shells include:

```text
zsh
fish
```

Zsh provides additional shell features and can be extended further using frameworks such as **Oh My Zsh**, which provides themes, plugins, aliases, and other quality-of-life improvements.

Terminal multiplexers such as:

```text
screen
tmux
```

allow multiple terminal sessions to be managed from a single terminal.

These tools can be particularly useful when:

- Administering remote systems
- Working through SSH
- Running long-lived processes
- Managing several simultaneous tasks
- Returning to existing terminal sessions later

Tools like these are not strictly necessary, but they can significantly improve terminal workflow once incorporated into regular use.

---

## Key Takeaways

Small command-line conveniences can have a significant impact on everyday Linux workflow.

Useful techniques reviewed today included:

```bash
less
history
!number
```

along with:

```text
Tab
Ctrl + r
```

Knowing how to search command history, autocomplete paths, inspect dotfiles, and efficiently navigate large text files reduces repetitive typing and makes terminal work considerably faster.

Another important lesson is that Linux shell configuration is largely stored in ordinary text files.

Files such as:

```text
~/.bashrc
~/.bash_history
```

provide both configuration and historical information about the user's shell environment.

Terminal multiplexers and enhanced shell environments also demonstrate how much the terminal experience can be customized around individual workflows.

---

## Personal Notes

Day 05 was mostly a refresher, as many of the shell navigation, history, and configuration concepts are already part of my normal Linux workflow.

I did spend some additional time experimenting with:

```bash
screen
tmux
```

Both tools were interesting to test and made the advantages of terminal multiplexing very clear.

Being able to maintain multiple terminal sessions from a single connection can make administrative work much easier, especially when working remotely or when several tasks need to remain active at the same time.

I can see tools like `tmux` and `screen` being particularly useful for:

- Maintaining multiple shell sessions
- Switching quickly between different tasks
- Keeping long-running commands active
- Working more efficiently over SSH
- Reducing the need for several separate terminal windows

I also already use **Zsh** along with **Oh My Zsh** as part of my normal Linux environment.

One of the things I appreciate most about Zsh and Oh My Zsh is the additional functionality and improved readability they can provide compared to a completely unconfigured shell.

Features such as enhanced prompts, command completion, plugins, and visual indicators make it easier to understand what is happening in the terminal at a glance.

Even small quality-of-life improvements can make long work or practice sessions more comfortable and easier on the eyes.

For anyone working through these notes who has only used a default Bash configuration, I would recommend experimenting with:

- Zsh
- Oh My Zsh
- `tmux`
- `screen`

None of these tools are required to work effectively with Linux, but they can make the terminal experience significantly more productive and enjoyable once you become comfortable with them.

---

## Status

✅ Day 05 Completed
