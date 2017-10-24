# Utility Commands

### Grab Url

`wget http://<url> -O url.txt -o /dev/null


### Remote Desktop

rdesktop <ip>

### SCP
Put File
`scp /tmp/file user@x.x.x.x:/tmp/file`

Get File
`scp user@x.x.x.x:/tmp/file /tmp/file`

### User Commands
Add User
`useradd -m <user>`

Change User Password
`passwd <user>`

Remove User
`rmuser <user>`

Record Shell
`script -a <outfile>`

### Find Related Commands

`apropos <subject>`

### Command History
View
`history`

Execute a Specific Line Number in History
!<num>
