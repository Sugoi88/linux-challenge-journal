# Day 03 - Power Trip!

## Objective

Understand Linux privilege levels and how administrative access is managed using `sudo`.

This lesson focused on the differences between regular users and the `root` account, performing administrative tasks safely, and reviewing several commands that require elevated privileges.

---

## Topics Covered

- Regular users vs. the `root` user
- The purpose of `sudo`
- Local vs. global system changes
- Changing user passwords
- Testing privileged file access
- Viewing login history
- Using a root shell
- Reviewing `sudo` activity
- Changing the system hostname
- Viewing and changing the system timezone
- Safe administrative practices

---

## Linux User Privileges

Linux systems generally separate users based on the level of access they require.

### Regular Users

A regular user normally has control over their own:

- Files
- Directories
- Processes
- Shell environment
- User-specific configuration

Regular users generally cannot make system-wide changes without additional privileges.

---

### Root

The `root` account is the Linux superuser.

It has unrestricted access to the system and can:

- Modify system configuration
- Access protected files
- Install or remove software
- Create and modify users
- Start and stop services
- Change permissions
- Modify networking configuration

Because `root` has unrestricted access, mistakes made while operating as `root` can affect the entire system.

For this reason, directly operating as `root` for normal administration is generally avoided when possible.

---

### Sudoers

A regular user can be granted permission to execute administrative commands using `sudo`.

For example:

```bash
sudo apt update
```

The command following `sudo` is executed with elevated privileges.

This allows administrators to use a normal account for everyday work and elevate privileges only when necessary.

---

## Local vs. Global Changes

A useful distinction when administering Linux is whether a change affects one user or the entire system.

### Local Change

A local change normally affects only the current user.

Examples include:

- Files inside the user's home directory
- Shell aliases
- User environment variables
- User-specific configuration files

### Global Change

A global change affects the wider system or multiple users.

Examples include:

- Installing system packages
- Changing the hostname
- Modifying system services
- Editing files under `/etc`
- Changing system-wide networking settings

Global changes generally require elevated privileges.

---

## Confirm Current User

```bash
whoami
```

Displays the username of the currently logged-in user.

---

## Changing a Password

A user can change their password using:

```bash
passwd
```

The command prompts for the current password followed by the new password.

Administrative users can also change passwords for other accounts when appropriate.

---

## Testing File Permissions

The `/etc/shadow` file contains protected account authentication information.

Attempting to read it as a regular user:

```bash
cat /etc/shadow
```

should normally result in a permission error.

Using `sudo`:

```bash
sudo cat /etc/shadow
```

allows an authorized administrative user to access the file.

This demonstrates how Linux permissions protect sensitive system resources.

---

## Running Administrative Commands

Some commands require elevated privileges.

For example:

```bash
reboot
```

may fail for an unprivileged user depending on the system configuration.

Running the command with elevated privileges:

```bash
sudo reboot
```

allows an authorized administrator to reboot the system.

After reconnecting, system uptime can be checked using:

```bash
uptime
```

---

## Login History

### View Login History

```bash
last
```

Displays previous login sessions.

A specific user can also be queried:

```bash
last username
```

For example:

```bash
last tankouban
```

---

### Failed Login Attempts

```bash
sudo lastb
```

Displays failed login attempts recorded by the system.

This can be useful when reviewing authentication activity or investigating potential unauthorized login attempts.

---

## Becoming Root Temporarily

An interactive root login shell can be opened using:

```bash
sudo -i
```

The shell prompt will normally change to indicate that commands are now being executed as `root`.

Return to the normal user account with:

```bash
exit
```

or:

```bash
logout
```

Using a root shell can be convenient when performing several administrative commands, but it also removes the safety of explicitly using `sudo` before each privileged command.

---

## `sudo -i` vs. `sudo -s`

Both commands provide a shell with root privileges, but they behave differently.

### `sudo -i`

```bash
sudo -i
```

Creates a root login shell and loads the root user's environment.

This more closely resembles logging directly into the system as `root`.

### `sudo -s`

```bash
sudo -s
```

Creates a shell with root privileges while retaining more of the current user's environment.

Understanding this distinction can be important when environment variables, paths, or configuration files affect administrative commands.

---

## Reviewing Sudo Activity

Recent `sudo` activity can be viewed through the system journal.

```bash
sudo journalctl -e /usr/bin/sudo
```

Linux logging makes it possible to review administrative activity rather than treating privileged actions as invisible events.

This is useful for:

- Troubleshooting
- Auditing
- Security investigations
- Determining when administrative commands were executed

---

## Changing the Hostname

The current hostname can be viewed using:

```bash
hostname
```

or:

```bash
hostnamectl
```

The system hostname can be changed using:

```bash
sudo hostnamectl set-hostname new-hostname
```

For example:

```bash
sudo hostnamectl set-hostname ubuntu-server-01
```

`hostnamectl` provides a modern method for managing the system hostname without manually editing multiple configuration files.

---

## Time and Timezone Management

View the current time and timezone configuration:

```bash
timedatectl
```

List available timezones:

```bash
timedatectl list-timezones
```

A timezone can be configured using:

```bash
sudo timedatectl set-timezone Region/City
```

For example:

```bash
sudo timedatectl set-timezone America/Detroit
```

Confirm the change with:

```bash
timedatectl
```

Timezone configuration is particularly important for:

- Log timestamps
- Scheduled tasks
- Troubleshooting
- Event correlation
- Distributed systems

Servers may also intentionally remain configured for UTC to provide a consistent time reference across environments.

---

## Administrative Safety

Administrative privileges should be used intentionally.

Some useful practices include:

- Work from a regular user account whenever possible.
- Elevate privileges only when necessary.
- Review commands before pressing Enter.
- Be especially careful with commands that modify or delete files.
- Verify configuration syntax before restarting services.
- Review logs when troubleshooting administrative changes.
- Test significant changes in non-production environments first.
- Avoid remaining inside a root shell longer than necessary.

The goal is not simply to gain administrative access, but to control when and how that access is used.

---

## Key Takeaways

The `root` account has unrestricted access to a Linux system, making it both powerful and potentially dangerous.

Using:

```bash
sudo
```

allows trusted users to perform administrative tasks while continuing to operate primarily as regular users.

Several useful administrative commands reviewed during this lesson included:

```bash
whoami
passwd
sudo
last
lastb
journalctl
hostnamectl
timedatectl
uptime
```

Privilege separation is an important part of both Linux administration and system security.

Understanding when elevated privileges are required, and avoiding unnecessary use of those privileges, reduces the possibility of accidental or unauthorized system changes.

---

## Personal Notes

Day 03 was completed without any issues or additional troubleshooting.

The concepts and commands covered were familiar from previous Linux use, so this lesson primarily served as reinforcement of privilege management and safe administrative practices.

---

## Status

✅ Day 03 Completed
