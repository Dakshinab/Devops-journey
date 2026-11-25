# 01 - Linux and WSL2

## What I did

I practiced the Linux basics on Ubuntu running in WSL2. I worked in this order:

1. Checked where I am and who I am (`pwd`, `whoami`, `uname -a`)
2. Made folders and files (`mkdir`, `cd`, `touch`, `ls -l`)
3. Learned file permissions. A new script failed with "Permission denied" until I added the run permission with `chmod`
4. Looked at users and groups (`id`, `/etc/passwd`, `/etc/shadow`)
5. Read files and searched inside them (`cat`, `head`, `tail`, `grep`, pipes)
6. Copied, moved, renamed and deleted files (`cp`, `mv`, `rm`)
7. Searched for files and programs (`find`, `which`)
8. Checked disk space and running programs (`df`, `du`, `ps`)
9. Started a background process and stopped it (`sleep 300 &`, `kill`)
10. Installed a tool with `apt`
11. Checked services and read logs (`systemctl`, `journalctl`, `/var/log`)

## Why it matters

Almost every cloud server runs Linux. DevOps work happens in the terminal: fixing permissions, finding errors in logs, checking if a service is up, and installing tools.

## Key commands

| Command | What it does |
|---------|--------------|
| `pwd`, `whoami`, `uname -a` | Where am I, who am I, what machine is this |
| `ls -l` | List files with owner, size and permissions |
| `chmod 600 file` | Set permissions. Read 4, write 2, run 1 |
| `id` | Show my user and groups |
| `grep -i -n word file` | Search a file, ignore case, show line numbers |
| `head`, `tail`, `tail -f` | First lines, last lines, follow a log live |
| `cmd1 \| cmd2` | Pipe: send the output of one command into the next |
| `find ~ -name "*.sh"` | Find files by name |
| `which bash` | Show which file runs when I type a command |
| `df -h`, `du -sh` | Free disk space, size of a folder |
| `ps aux`, `kill PID` | List running programs, stop one |
| `sudo apt update`, `sudo apt install` | Refresh the package list, install software |
| `systemctl status name` | Is a service running, and since when |
| `journalctl -u name` | Read the log of one service |

## What I learned

- Permissions: keys are `600` or `400`, scripts are `750` or `755`, and I never use `777`. This is least privilege.
- The `x` in `/etc/passwd` means the real password hash is in `/etc/shadow`, which only root can read.
- A shell is the program that reads my commands. A terminal is only the window.
- `rm` has no recycle bin, so I check `pwd` and `ls` first.
- The 1 TB disk size in WSL2 is only a limit. The real space is what is free on the Windows drive.
- When a service fails: `systemctl status`, then `journalctl -u name`, then `/var/log`.
- `apt install` needs `sudo` because it writes into system folders. A package source with a missing key is refused, which is a security feature.
