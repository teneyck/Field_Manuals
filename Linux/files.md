# Files


### File Operations

diff two files `diff <file1> <file2>`
Overwrite a file `rm -rf <dir>`
Complete removal `shred -f -u <file>`
Date manipulation `touch -r <ref_file> <file>`
Date set `touch -t <YYYYMMDDHHSS> <file>`

### Drive Operations

List connected drives `sudo fdisk -l`
Mount a drive `mount /dev/sda<#> /mnt/<name>`


### Unusual SUID files

`find / -uid 0 - perm -4000 - print`

### Unusual large files

` find / size +10000k -print`

### Hidden or Obfuscated

```
find / -name " " - print
find / -name ".. " -print
find / -name ". " -print
find / -name " " -print
```

### Unlinked Files w/ Processes

`lsof +L1`


### Orphaned Files

`find / -nouser -print`

### Hash a file

```
sha1sum <file>
md5sum <file>
```


### TAR

Create .tar from files `tar cf <file>.tar <files>`
Extract .tar `tar xf file.tar`
Create .tar.gz `tar czf <file>.tar.gz <files>`
Extract tar.gz `tar xzf filae.tar.gz`
Create .tar.bz2 `tar cjf file.tar.bz2 files`
Extract .tar.bz2 `tar xjf file.tar.bz2`
