# Files and Registries

## Forensics

### File Free Space usage:

`dir c:\`

### Strange Startup Programs

```
Software\Microsoft\Windows\CurrentVersion\Run
Software\Microsoft\Windows\CurrentVersion\RunOnce
Software\Microsoft\Windows\CurrentVersion\RunOnceEx
```

#### Using the GUI:

`regedit`

#### Using the Command prompt:

'reg query'

### Cheksum a file

`FCIV -md5 -sha1 path\filename.ext`


TODO: Find PowerShell equivalents for cmd.execution_count
