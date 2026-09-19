# Day 02 - Basic Navigation

## Objective

Build confidence navigating the Linux filesystem from the command line and review the tools available for finding documentation about commands.

The lesson also covers basic directory and file manipulation, along with several shortcuts that can make terminal navigation more efficient.

---

## Topics Covered

- Using Linux documentation
- Navigating the filesystem
- Absolute and relative paths
- Listing files and directories
- Hidden files
- Creating and removing directories
- Creating, moving, and deleting files
- Using directory navigation shortcuts
- Using `pushd` and `popd`

---

## Command Documentation

Linux provides several built-in ways to learn more about commands without leaving the terminal.

### `man`

```bash
man command
```

Example:

```bash
man ls
man cp
man mv
```

`man` displays the manual page for a command and provides detailed information about its syntax and available options.

---

### `help`

```bash
help command
```

Some commands are built directly into the shell and may not have traditional manual pages.

For example:

```bash
help export
```

---

### `type`

```bash
type command
```

Used to identify how the shell interprets a command.

Example:

```bash
type export
```

This can help determine whether something is a shell builtin, executable, alias, or another type of command.

---

### `apropos`

```bash
apropos "search term"
```

Useful when the exact command name is unknown but the general function is known.

For example:

```bash
apropos "working directory"
```

A similar search can be performed with:

```bash
man -k "working directory"
```

---

## Filesystem Navigation

### Print Working Directory

```bash
pwd
```

Displays the full path of the current working directory.

---

### Change Directory

```bash
cd /var/log
```

Moves into the specified directory.

Move up one directory level:

```bash
cd ..
```

Return to the current user's home directory:

```bash
cd
```

or:

```bash
cd ~
```

Return to the previously visited directory:

```bash
cd -
```

---

## Absolute vs Relative Paths

An **absolute path** begins at the filesystem root:

```bash
cd /var/log
```

A **relative path** begins from the current working directory.

For example, if already inside `/var`:

```bash
cd log
```

Both examples can lead to the same directory, but they reference it differently.

---

## Listing Files and Directories

Basic listing:

```bash
ls
```

Long format:

```bash
ls -l
```

Include hidden files:

```bash
ls -a
```

Multiple options can be combined:

```bash
ls -ltra
```

This displays files in long format, includes hidden files, sorts by modification time, and reverses the order.

Files and directories beginning with `.` are considered hidden by convention.

Examples include:

```text
.bashrc
.profile
.ssh
```

---

## Directory Manipulation

### Create a Directory

```bash
mkdir test
```

Create nested directories:

```bash
mkdir -p projects/linux/test
```

---

### Move or Rename a Directory

```bash
mv source destination
```

Example:

```bash
mv test ~/projects/
```

---

### Remove an Empty Directory

```bash
rmdir test
```

---

### Remove a Directory and Its Contents

```bash
rm -r directory
```

This command should be used carefully because files removed from the command line generally do not pass through a graphical trash or recycle bin.

---

## Basic File Manipulation

### Create an Empty File

```bash
touch test.txt
```

---

### Move or Rename a File

```bash
mv test.txt new-name.txt
```

---

### Remove a File

```bash
rm test.txt
```

---

## Directory Stack Navigation

One of the more useful concepts reviewed during this lesson was the directory stack.

### `pushd`

```bash
pushd /var/log
```

`pushd` changes to another directory while saving the previous directory in a directory stack.

Additional locations can be added:

```bash
pushd /etc
pushd /dev
```

---

### `popd`

```bash
popd
```

`popd` removes the current directory from the stack and returns to the previous stored location.

---

### View the Directory Stack

```bash
dirs
```

This displays the directories currently stored in the directory stack.

Example workflow:

```bash
pushd /var/log
pushd /etc
pushd /dev

dirs

popd
popd
```

This makes it possible to move between several working directories without repeatedly typing complete paths.

---

## Key Takeaways

Linux command-line navigation relies heavily on understanding the filesystem hierarchy and knowing where you are currently working.

Commands such as:

```bash
pwd
cd
ls
mkdir
mv
rm
```

form the foundation of everyday terminal usage.

The built-in Linux documentation tools are equally important. Rather than memorizing every possible option for every command, knowing how to use tools such as:

```bash
man
help
type
apropos
```

makes it possible to quickly find the information needed while working.

---

## Personal Notes

Most of the basic navigation and file manipulation covered during Day 02 was already familiar from regular Linux use.

The most useful takeaway was revisiting:

```bash
pushd
popd
dirs
```

Once these commands become part of the normal workflow, they can be significant time savers.

Instead of repeatedly typing long paths or manually navigating back and forth between directories, `pushd` allows useful locations to be placed onto a directory stack and `popd` makes it easy to return through them.

This becomes especially useful when working across several directories during administration, troubleshooting, development, or configuration work.

It is one of those Linux features that is easy to overlook but becomes extremely convenient once it becomes habitual.

---

## Status

✅ Day 02 Completed
