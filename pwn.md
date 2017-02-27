# Pwn

## Privilege escalation

This page has a great summary/cheatsheet of many different things to try when we have already a shell: [Basic Linux Privilege Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/). Specially things like `sudo -l` to list what you can do, or searching for files with _advanced_ Linux file permissions (`SUID`, `GUID`):

```
find / -perm -g=s -type f 2>/dev/null    # SGID (chmod 2000) - run as the group, not the user who started it.
find / -perm -u=s -type f 2>/dev/null    # SUID (chmod 4000) - run as the owner, not the user who started it.
```

## Escaping a restricted shell

This is a well-known escape using `vim`:

```
:set shell=/bin/bash
:shell
```

With `rvim`, that doesn't allow the previous escape, it might still be possible to run code using `:python` or `:lua` modules. To list installed features use `:version`. 

