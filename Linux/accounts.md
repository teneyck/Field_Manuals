# Accounts

## Forensics

### Accounts by UID

`sort -nk3-t: /etc/passwd | less`

### UID 0 accounts

`egrep ':0+:' /etc/password`

`getent passwd | egrep ':0+:'`

### Orphaned Files

`find / -nouser -print`
