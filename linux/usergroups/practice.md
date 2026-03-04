# Linux User and Group Management Comprehensive Practice Guide

This guide provides a hands-on demonstration of user and group management commands on an Ubuntu server, covering topics from the notes.

## 1. Basic User and Group Creation
We'll start by creating a user and a group, and adding the user to the group.

### a. Create a user
```bash
sudo useradd johndoe
sudo passwd johndoe
```

### b. Create a group
```bash
sudo groupadd developers
```

### c. Add user to group (as a secondary group)
```bash
sudo usermod -aG developers johndoe
groups johndoe
```

## 2. Managing Primary and Secondary Groups

### a. Change a user's primary group
To change `johndoe`'s primary group to `developers`:
```bash
sudo usermod -g developers johndoe
```

### b. Add multiple secondary groups
To add `johndoe` to the `testers` and `staging` groups:
```bash
sudo usermod -aG testers,staging johndoe
```

## 3. Advanced User Creation

### a. Create a user with a specific home directory and shell
```bash
sudo useradd -m -d /var/www/janesite -s /bin/zsh janedoe
```

### b. Create a user with a specific UID
```bash
sudo useradd -u 1500 mark
```

### c. Create a system user
```bash
sudo useradd -r appsvc
```

## 4. Modifying Users

### a. Change a user's login name
```bash
sudo usermod -l newname oldname
```

### b. Lock a user account
```bash
sudo usermod -L janedoe
```

### c. Unlock a user account
```bash
sudo usermod -U janedoe
```

### d. Set an account expiration date
```bash
# Note: The date format may vary. Use YYYY-MM-DD for modern systems.
sudo usermod -e 2024-12-31 mark
```

## 5. Password Aging

### a. Force a user to change their password on next login
```bash
sudo chage -d 0 johndoe
```

### b. Set password expiration policies
```bash
# Set max password age to 90 days
sudo chage -M 90 johndoe

# Set password to never expire
sudo chage -M -1 johndoe
```

### c. Check password aging information
```bash
sudo chage -l johndoe
```

## 6. Advanced Group Management

### a. Rename a group
```bash
sudo groupmod -n newgroupname oldgroupname
```

## 7. Deleting Users and Groups

### a. Remove a user from a group
```bash
sudo deluser johndoe developers
```

### b. Delete a user
```bash
# -r flag removes the user's home directory
sudo userdel -r johndoe
```

### c. Delete a group
```bash
sudo groupdel developers
```
