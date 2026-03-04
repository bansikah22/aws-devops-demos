# User and Group Management in Linux

This document provides a summary of commands for managing users and groups in Linux, based on the provided notes.

## Table of Contents

- [User Management](#user-management)
  - [Creating Users](#creating-users)
  - [Setting Passwords](#setting-passwords)
  - [Deleting Users](#deleting-users)
  - [Modifying Users](#modifying-users)
- [Group Management](#group-management)
  - [Creating Groups](#creating-groups)
  - [Adding Users to Groups](#adding-users-to-groups)
  - [Managing Group Passwords](#managing-group-passwords)
  - [Deleting Users from Groups](#deleting-users-from-groups)
  - [Modifying Groups](#modifying-groups)
  - [Deleting Groups](#deleting-groups)

---

### User Management

#### Creating Users

- **`sudo useradd john`**: Creates a new user named `john`. A new group `john` is automatically created, and the user's home directory is `/home/john` with `/bin/bash` as the default shell.
- **`ls -la /etc/skel`**: Lists the content of the `/etc/skel` directory, which contains default files for new user home directories.
- **`useradd --defaults`** or **`useradd -D`**: Displays the default user creation settings.
- **`cat /etc/login.defs`**: Shows the configuration file for login defaults.
- **`sudo useradd --shell /bin/othershell --home-dir /home/otherdirectory john`**: Creates a user `john` with a specified shell and home directory.
- **`sudo useradd -s /bin/othershell -d /home/otherdirectory john`**: A shorter version of the previous command.
- **`sudo useradd --uid 1100 smith`**: Creates a user `smith` with a specific UID.
- **`sudo useradd --system sysacc`**: Creates a system account. System account UIDs are typically smaller than 1000.

#### Setting Passwords

- **`sudo passwd john`**: Sets the password for the user `john`. You will be prompted to enter and confirm the password.

#### Deleting Users

- **`sudo userdel john`**: Deletes the user `john`.
- **`sudo userdel --remove john`**: Deletes the user `john` and removes their home directory.

#### Modifying Users

- **`sudo usermod --move-home -d /home/otherdir john`**: Moves the home directory of user `john` to a new location.
- **`sudo usermod -d /home/newdir -m john`**:  Moves the home directory of user `john` to a new location.
- **`sudo usermod --login jane john`**: Changes the username of `john` to `jane`.
- **`sudo usermod -s /bin/othershell jane`**: Changes the shell for user `jane`.
- **`sudo usermod --lock jane`** or **`sudo usermod -L jane`**: Locks the user account `jane`.
- **`sudo usermod --unlock jane`** or **`sudo usermod -U jane`**: Unlocks the user account `jane`.
- **`sudo usermod -e 2021-12-10 jane`**: Sets the expiration date for the user account `jane`. The date format is `YYYY-MM-DD`.
- **`sudo usermod -e "" jane`**: Removes the expiration date for the user account `jane`.
- **`sudo chage --lastday 0 jane`**: Forces the user `jane` to change their password on the next login.
- **`sudo chage --maxdays 30 jane`**: Sets the maximum number of days a password for user `jane` is valid.
- **`sudo chage --maxdays -1 jane`**: Sets the password for user `jane` to never expire.
- **`sudo chage --list jane`**: Displays the password aging information for user `jane`.

---

### Group Management

#### Creating Groups

- **`sudo groupadd developers`**: Creates a new group named `developers`.

#### Adding Users to Groups

- **`sudo gpasswd --add john developers`**: Adds the user `john` to the `developers` group.

#### Managing Group Passwords

- **`sudo gpasswd -a john developers`**: Another way to add a user to a group.

#### Deleting Users from Groups

- **`sudo gpasswd --delete john developers`**: Removes the user `john` from the `developers` group.

#### Modifying Groups

- **`sudo usermod -g developers john`**: Changes the primary group of the user `john` to `developers`.
- **`sudo usermod --gid developers john`**:  Another way to change the primary group of a user.
- **`sudo groupmod --new-name programmers developers`**: Renames the `developers` group to `programmers`.
- **`sudo groupmod -n programmers developers`**: A shorter version of the previous command.
- **`sudo usermod -gid john john`**:  Sets the primary group of the user `john` back to `john`.

#### Deleting Groups

- **`sudo groupdel programmers`**: Deletes the `programmers` group. A group cannot be deleted if it is the primary group for any user.
