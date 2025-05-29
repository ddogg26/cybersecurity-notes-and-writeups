### `ssh bandit.labs.overthewire.org -p 2220 -l bandit#`

#### bandit 0 - bandit0
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
I like to leave the login flag at the end of the command, which makes it easier to press 'up' on the keyboard and backspace once to change which bandit user I'm logging into. Just makes things quicker
#### bandit 0 -> 1 - ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- `cat readme`
Not much going on here, just make sure you know ls (list) and cat (concatenate)
#### bandit 1 -> 2 - 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
- `cat ./-`
- `cat /home/bandit1/-`
#### bandit 2 -> 3 - MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
- `cat "spaces in this filename"`
- `cat spaces\ in\ this\ filename`
#### bandit 3 -> 4 - 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
- `ls -a`
- `cat ...Hiding-From-You`
Pretty much by default, I'm always using `ls -la` in every directory I'm looking in, because you never know when there might be hidden files. Built into some linux distros are quick aliases you can use to speed things up. For example, in kali, you can type `ll`, and it corresponds to `ls -la`
#### bandit 4 -> 5 - 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
 - `file ./*`
 - `file ./-file*`
#### bandit 5 -> 6 - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
- `find -size 1033c`
#### bandit 6 -> 7 - morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
- `find / -size 33c -user bandit7 -group bandit6 2>/dev/null`
#### bandit 7 -> 8 - dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
- `cat data.txt | grep millionth`
#### bandit 8 -> 9 - 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
#### bandit 9 -> 10 - FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
* `base64 -d <file>`
#### bandit 10 -> 11 - dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
* ROT13
#### bandit 11 -> 12 - 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
* Because it is a complete hex dump, there are tools that can be used to restore the original binary file
* `xxd -r <hexdump> > newfile`
* this gives you a
#### bandit 12 -> 13 - FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
#### bandit 13 -> 14 - `ssh bandit.labs.overthewire.org -p 2220 -i sshkey.private -l bandit14`
#### bandit 14 -> 15 - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
#### bandit 15 -> 16 - 
#### bandit 16 -> 17 - 
