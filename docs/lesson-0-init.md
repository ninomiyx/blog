# Project Setup

## SSH Keys

SSH is short Security SHell. It's authenticated by public / private keys -- this is a encryption system which data encrypted public key can only be decrypted by private key.

In Linux OS, a user's public / private keys are storged in `~/.ssh` directory.

`~` is Home directory, equal to `/home/USER_NAME`. root user's home is `/root`.

We can run `ssh-keygen` to generate a pair of public / private keys. Default to save the keys to `~/.ssh/id_rsa` (private key) and `~/.ssh/id_rsa.pub` (public key).

```
yuxin:~ $ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ec2-user/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/ec2-user/.ssh/id_rsa.
Your public key has been saved in /home/ec2-user/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:y9/RO90gkuwOkS27KqQHWkqQ2BcOJ82KzJHtnia41gI ec2-user
The key's randomart image is:
+---[RSA 2048]----+
|  oo             |
| oo.=            |
|++o* .           |
|=oo.o    o       |
|o ...   S...     |
|Eoo+.  . =+ ...  |
|o=++    =. ....o.|
|+o..o    +.. ...o|
|. .. .....o . .. |
+----[SHA256]-----+
```

`SHA256` is a hash function, it to generate a summary of the data. For easier comparing of different keys, `SHA256` is being truned into text graph.

We can run `cat /home/ec2-user/.ssh/id_rsa.pub` to view the public key. And copy the key to [Github](https://github.com/settings/ssh/new) (`Settings` / `SSH / GPG Keys` / `New SSH Key`)


## Create and clone a repository (repo)

- In Github navigation bar, `Plus button` / `New repository` to create a repo.
- Open the newly created repo, click `Clone or download` to copy the SSH address of the repo.
- Run `git clone SSH_ADDRESS`
- `git status` to view local changes
- `git add FILE_NAME` to add a file to local git repo's stage
- `git commit` to commit (save) the staged files to local git repo
- `git push` to push local git repo data to remote
- `git log` to view the command history
- `git diff` to see recent change diffs <br>
  `git diff --cached` to see added diffs
- `git config --global user.name "xxx"` to change global user name, which is used in commit message <br>
  `git config --global user.email "xxx@xxx"` to change global user email  

## Genernal knowledge

- files / directories named starting with a dot `.` is hidden by default.
- in `ls -l` command the first column is about the `mode` (permission) of the file 
  - the first letter is the type of the file / directory
    `-` is file
    `d` is directory
    `l` is a symbol link, a pointer to another file or directory
  - the following 9 letters are grouped into 3-3-3 groups
    in each group, rwx, read / write / execute. Execute means a file can be executed or directory can be listed
    the three groups are for owner / group / other.
- in `ls -l`, the 3rd and 4th are the owner and the group owner of the file; 5th is the size of the file / directory; 6th is the last modified time
- name `.` means current directory / `..` means parent directory


## Genernal commands

- `pwd` print current working directory
- `cd` change directory, switch current working directory
- `ls` list files / directories in the current directory
  `-l` to list as a list, alias to `ll`
  `-a` to list all files / directories (including those hidden)
  `-a` + `-l` can be typed as `-al`, so as some other commands
- `mv` move (rename) file or directory
- `rm` delete file or empty directory
  `-r` for deleting non-empty directory (r is short for recursive)
- `chmod` change a file / directory's mode
  `600` / `660` / `664`
  `g-r-w` / `o-r` / `g+r`
- `chown` change the ownership of the file / directory
- `touch` to create an empty file
- `man COMMAND` to find the manual of a comman
  `q` for exit the man command
  `[]` means optional parameter