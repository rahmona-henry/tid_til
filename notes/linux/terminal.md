[backend](../backend.md) | [linux](index.md) | [tools](../tools.md)

## Nix Terminal (linux/unix)
- **[Git / Github](git-github.md)**
- **[network tools](network.md)**
- [terminal keyboard shortcuts](#terminal-keyboard-shortcuts)
- [basic commands](#basic-commands)
- [ls](#ls)
- [cd](#cd)
- [rm](#rm)
- [ln](#ln)
- [outputting](#outputting)
- [piping](#piping)
- [redirection](#redirection)
- [text editors](#text-editors)
- [searching](#searching)([find](#find), [grep](#grep), [sed](#sed))
- [chmod](#chmod), [chown](#chown)
- [system](#system) (help, aliases, shutdown..)
- [sudo & su](#sudo--su)
- [managing applications](#managing-applications)
- [disk usage](#disk-usage)
- [tmux](#tmux-terminal-multiplexer)
- [BASH scripts](#bash-scripts)
- [user account management](#user-account-management)

## terminal keyboard shortcuts
- `ctrl alt t`: open terminal window
- `ctrl shift t`: open new tab
- `ctrl shift n`: open new window
- `ctrl shift w`: close tab
- `ctrl shift q`: close terminal window
- `ctrl pageup` ( `ctrl + fn + up` ): next tab
- `ctrl l`: clear terminal
- `ctrl + r`: reverse search. ctrl + r, then start typing a command you have used recently & it will come up, then press enter. preferable to having to retype long commands again & again.
- `ctrl a`: start of line
- `ctrl e`: end of line
- `ctrl p`: previous command
- `ctrl n`: next

## basic commands
- `pwd`: print working directory

- `clear`: clear screen (also ctrl + l)

- `mv`: move file(s), source file(s) then destination, e.g. `mv filename ~`

- `cp`: copy file(s), source file(s) then destination

- `touch`: creates empty file, `touch stuff.txt`

- `wc`: 'Word Count' lines, words, characters, eg. `cat filename | wc`

- `mkdir`: creates directory, e.g. `mkdir dirname`. `mkdir -p newfolder/child/chilOfChild` creates a path of folders (subfolders)

- `rmdir`: removes empty directories, e.g. `rmdir dirname`

- `sort`: Orders Alphabetically, `sort filename.*` or `cat lakes.txt | sort > sorted_lakes.txt`

- `uniq`: filters out adjacent duplicate lines & outputs contents, `uniq filename`

- `file /user/home/filename.txt`: tells you document type

- `history`: displays recent commands. `history -c`: clears history (stored in `~/.bash_history` or `~/.zsh_history`)


#### ls
- `ls` - list files (`-l` long form, `-a` hidden files & directories, `-t` sort by time modified)
- `ls /bin`: list files/folders in /bin

#### cd
- `cd ../..`: change directory
- `cd /` goes to root (as does `/`)
- `cd` goes to home

#### rm
- `rm` ( remove files & directories, -r recursive )
- `rm -rf dirname`: removes non-empty dir ( recursive & force )

#### ln
creates links to files or folders
- `ln file1 yea`: creates hard link to file1. link is called yea
- `ln -s file1 yea`: creates symlink (soft) to file1. If file1 is deleted, link will not work..
- [more info](http://www.unixtutorial.org/commands/ln/)

## outputting
- `cat`: outputs contents of file to terminal, `cat filename`

- `less`: Output file contents to screen, e.g. `less filename`. see also 'more'

- `more`: prints out file to screen, page by page

- `head`: first 10 lines of a file, e.g. `head filename`

- `tail`: last 10 lines of a file. also `tail -f filename`: follows a file.. (as it changes over time)

### piping
`|` (pipe) pipes output (stdout / 1) of one command to the input (stdin / 0) of another (see basic commands for other examples)

Syntax:

`ps aux | grep nginx`: check CPU usage for a process (nginx)

`sort deserts.txt | uniq > uniq-deserts.txt`

sort deserts.txt, pipe to `uniq`, redirect to newfile.


### redirection
redirect output of a command to a file

`>`

Syntax:
- `cat filename > otherFilename`: outputs contents of filename to otherFilename (overwrites anything in otherFilename)
- `cat filename >> otherFilename`: append to file (instead of overwriting)

redirect output of a file to the input of a command

`<`

Syntax:
- `prog1 < file.txt`

### standard input/output/error
- 0 represents stdin
- 1 represents stdout
- 2 represents stderr

`ls -alh nonexistentFile 2> error.txt`: redirects error (stderr) returned from listing non-existent file to error.txt

## Searching

### find
Syntax: `find ~/Downloads theFileImLookingFor`: Finds files/directories.
- `find -iname "markdown.*"`: search for files called markdown (`-iname`: case-insensitive)
- `find /home -iname "markdown.*"`: search for files in /home called markdown
- use `-type` & a letter, such as `f`: files, `d` directories, `l`: symbolic links etc. e.g. `find / -type d -iname "filename"`

hint: pipe results to less

### grep
- 'G'lobal 'Re'gular expression 'P'rint (regex), used to look for line that matches a pattern inside files
- `grep "foo" words.txt` or `grep -i "foo" words.txt` or `grep -R searchterm /home/user/`
- `-i`: case-insensitive
- `-R`: recursive
- `-v`: invert
- `-n`: line number
- `^`: start of line
- `$`: end of line
- `..cept` finds `accept`, `except`

### sed
'stream editor', accepts standard input and modifies it based on an expression, before displaying it as output, for filtering & transforming text

---

### cut
if we have a file, file1.txt which contains:
```
user:we
user:love
user:linux
```

we can run `cat file1.txt | cut -d: -f2` which will output

```
we
love
linux
```
`-d`: delimiter, `-f2`: second field

### text editors
- `nano path/filename`: Open file in Nano editor ( ctrl + O to save, ctrl + X to exit )

- `vi path/filename`: open file in Vim. Vim has 2 modes, 'esc' & 'i' alternate between modes. i is text mode, esc then `:q` then enter to quit. `:wq` to write to file & quit

### chmod
'change mode' change the access permissions to file system objects (files and directories).
- `chmod`: change mode, modify permission string
- `chmod +x`: adds execution rights
- `chmod -x`: removes execution rights

`chmod 644 filename` or `chmod 777 filename`

### chown
'change owner' or group of object
- `chown -R ghost:ghost .` chown recursively, group: ghost, user:ghost, `.` is current dir

## system
- 'man': manual pages. Use like: `man ls` or `man uniq` for manual pages on the ls or uniq commands
- help. to get help on a command type `commandName --help`, e.g. `ls --help` for help on ls
- `$`: represents prompt in BASH
- `.`: represents current directory
- `..`: represents parent directory, `cd ..`: change to parent directory
- ` ~`: (tilde) represents users home directory eg. `/home/user`, can use in relative paths e.g. `~/Documents/` is the same as `/home/user/Documents`
- `~/.bash_profile`: used to store environment settings for terminal (source ~/.bash_profile activates changes))

### system commands
- `tty`: displays the virtual terminal you are using..
- `whoami`: displays username
- `who am i`: displays username & terminal you are in.
- `hostname`: displays hostname (name of computer)
- `uname`: print system information. `uname -a` prints all
- `service udev status`: Check if 'udev' service is running (on older machines)
- `systemctl status udev`: Check if 'udev' service is running (on newer machines)
- `ps aux`: report snapshot of current processes. `a`: all, `u`: convert userid's to usernames, `x`: show processes not attached to a terminal (tty)
- `ps aux | grep nginx`: check CPU usage for a process (nginx)
- `top`: check CPU usage for a processes
- `w`: shows who is logged in & what they are doing

### shell
- `echo $0`
- `echo $SHELL`
- `echo "$$"`: to find the process ID (PID) of the current instance of shell
- `ps -p <PID>`: to find the process having the PID
- `ps -p "$$"`: to do this in one command
- `bash`: to change to BASH shell, `zsh`: to change to zsh shell (if installed)

### sudo / su
`su`: superuser. Typing `su` followed by root account password (if it has been set up), will log in as superuser/root user. To exit type `exit`.

`sudo` will just allow you superuser access for a single command.. e.g. `sudo apt-get install wine`. This is safer. The OS will remember your password for 15 minutes. If you haven't set up root account & password, you can log in as superuser with `sudo su` using just your user password.

### managing applications
installing / uninstalling / updating / upgrading
- `apt-cache search searchterm`: search repositories for search term (search through package names & descriptions)

- `sudo apt-get install packagename`: Install a package/program

- `sudo apt-get remove packagename`: Remove a package/program

- `sudo apt-get update`: update repo's (retrieve new lists of packages)

- `sudo apt-get upgrade`: install updates

- `sudo add-apt-repository ppa:numix/ppa`: add repository

- `sudo apt-get autoremove`: remove dependencies for programs which are no longer installed

- `cat /etc/apt/sources.list`: displays repositories subscribed to

- `ls /usr/share/applications | awk -F '.desktop' ' { print $1}' - > ~/Desktop/applications.txt`: list installed applications & output to file on desktop

- `dpkg -L packagename`: lists all files 'owned' by a package

### disk usage
- `df -ah` `-a`: all, `-h`: human-readable
- `du -hs ./path/to/dir` ( `du` = disk usage, `h` = human-readable, `s` = summary ) recursive summary of folder & subfolders..
- `lsblk`: list info about block devices
- `baobab`: open disk usage analyser

### aliases
- 'alias' is another name for keyboard shortcut in the terminal, defined in .bashrc or .zshrc etc as
- `alias tek="cd ~Documents/tech"`
- `alias | wc -l`: number of aliases

### shutdown
`shutdown` `shutdown -h`: halt/turn off. `shutdown -r +30`: restart in 30 minutes, `shutdown -h now`: turn off now

also `poweroff` or `init 0` do the same

`init 6`: reboot

### tmux (terminal multiplexer)
- `tmux`  to enter tmux
- `ctrl + b` then `?` for help (list commands)
- `ctrl + b` then `c` to create new window (`p`: previous, `n`: next, `w`: list all)
- `%`: split horizontally, `"`: split vertically
- `exit`: to exit

### BASH scripts
starts with hashbang (`#!`) & reference to thing that runs the script e.g.
- `#! /bin/bash`: bash script
- `#! /usr/bin/env node`: node script

- [Beginners Bash Scripting](https://help.ubuntu.com/community/Beginners/BashScripting)

### User Account Management
see '/etc/passwd', '/etc/shadow' & '/etc/group'

##### useradd
- `useradd userName`: creates a user. `-m`: create a home dir, `-d`: define a path for it, `-s`: default shell..

    e.g. `useradd mymble -m -d /home/mymble -s /bin/bash`


- `userdel userName`: delete user
- `passwd userName`: sets a password for a user.
- usermod -L userName: locks an account
- `usermod -U userName`: unlocks

---

See also [Git / GitHub](../git-github.md)
