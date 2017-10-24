# Network Usage

## Forensics

### Look at file shares:

`net view \\127.0.0.1`

### List open SMB Sessions local:

`net session`

### List outbound open SMB sessions:

`net use`

### Look at NetBios activity:

`nbtstat -na`

### Unusual listening:

`netstsat -na`

#### Continuous

`netstat -na 5`

#### With owner:

`netstat -nao 5`

#### With executables and dlls:

`netstat -naob 5`

### Firewall Configuration

`netsh advfirewall firewall show rule name=all`
