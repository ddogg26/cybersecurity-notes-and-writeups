### `ssh bandit.labs.overthewire.org -p 2220 -l bandit#`

### General Tips
- the `man` command is very helpful when learning about other commands
	- **Example**: `man ls` will show you a ton of information about the `ls` command and how it's used
- If the `man` command is too much information, try appending `--help` to the command you want to learn about
	- **Example**: `cat --help` will you give a summarized version with what flags can be used with `cat`
- Tab autocomplete is your friend! When working with long filenames or extensive directory paths, just press tab as you're typing it out and for the most part, Linux should be able to handle it and finish what you were typing
	- **Example:** `cat really-sup` ***tab press*** --> `cat really-super-long-filename`

#### bandit 0 - bandit0
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
I like to leave the login flag at the end of the command, which makes it easier to press 'up' on the keyboard and backspace once to change which bandit user I'm logging into. Just makes things quicker
#### bandit 0 -> 1 | ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- `cat readme`
Not much going on here, just make sure you know ls (list) and cat (concatenate)
#### bandit 1 -> 2 | 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
- `cat ./-`
- `cat /home/bandit1/-`
Because the filename is a dash, Linux thinks that you are trying to give a flag for a command. You'll need to either provide the absolute or relative path so Linux knows that you are trying to access a file
#### bandit 2 -> 3 - MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
- `cat "spaces in this filename"`
- `cat spaces\ in\ this\ filename`
Linux doesn't like spaces in filenames because it interprets each word as a different file or argument for the initial command. You can either use quotes or the backslash (escape character) to let Linux know that the spaces are a part of the filename. The backslash basically says "Hey Linux! Whatever comes after me is a string character, so don't take it into account!"
#### bandit 3 -> 4 - 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
- `ls -a`
- `cat ...Hiding-From-You`
Pretty much by default, I'm always using `ls -la` in every directory I'm looking in, because you never know when there might be hidden files. Built into some Linux distros are quick aliases you can use to speed things up. For example, in kali, you can type `ll`, and it corresponds to `ls -la`
#### bandit 4 -> 5 - 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
 - `file ./*`
 - `file ./-file*`
 The file command will give you information about what the contents of a file are. Because of the dashes at the beginning of the filenames, you'll need to use the relative or absolute file paths again. We see that only 1 file has ASCII text. (human readable text) If you try to cat the non ASCII files, you'll see it's just gibberish.
#### bandit 5 -> 6 - HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
- `find -size 1033c`
The find command has many options to filter out different types of files. Although bandit gives us 3 filters to look for, in this case, just the size one will do. the letter after the filesize, `c` in this case, determines what unit of size to use. 
	- `c` for bytes
	- `w` for 2 byte words
	- `k` for kibibytes (kibibyte=1024 bytes, kilobyte=1000 bytes)
	- `M` for mebibytes
	- etc.
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
