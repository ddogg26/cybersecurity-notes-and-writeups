### `ssh bandit.labs.overthewire.org -p 2220 -l bandit#`

### General Tips
- the `man` command is very helpful when learning about other commands
	- **Example**: `man ls` will show you a ton of information about the `ls` command and how it's used
- If the `man` command is too much information, try appending `--help` to the command you want to learn about
	- **Example**: `cat --help` will you give a summarized version with what flags can be used with `cat`
- Tab autocomplete is your friend! When working with long filenames or extensive directory paths, just press tab as you're typing it out and for the most part, Linux should be able to handle it and finish what you were typing
	- **Example:** `cat really-sup` ***tab press*** --> `cat really-super-long-filename.txt`
- The **Pipe** operator `|` is used to string multiple commands together. The output of 1 command is then **piped** into the input of the next command
	- **Example:** `cat flag.txt | grep ctf` will send the output of the `cat` command (the contents of the file) to the input of the `grep` command, which will then find all instances of the word **ctf** in the text

#### bandit 0
- bandit0
- `ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
- I like to leave the login flag at the end of the command, which makes it easier to press 'up' on the keyboard and backspace once to change which bandit user I'm logging into. Just makes things quicker
#### bandit 0 -> 1
- ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
- `cat readme`
- Not much going on here, just make sure you know ls (list) and cat (concatenate)
#### bandit 1 -> 2
- 263JGJPfgU6LtdEvgfWU1XP5yac29mFx
- `cat ./-`
- `cat /home/bandit1/-`
- Because the filename is a dash, Linux thinks that you are trying to give a flag for a command. You'll need to either provide the absolute or relative path so Linux knows that you are trying to access a file directly
#### bandit 2 -> 3
- MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
- `cat "spaces in this filename"`
- `cat spaces\ in\ this\ filename`
- Linux doesn't like spaces in filenames because it interprets each word as a different file or argument for the initial command. You can either use quotes or the backslash (escape character) to let Linux know that the spaces are a part of the filename. The backslash basically says "Hey Linux! Whatever comes after me is a string character, so don't take it into account!"
#### bandit 3 -> 4
- 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
- `ls -a`
- `cat ...Hiding-From-You`
- Pretty much by default, I'm always using `ls -la` in every directory I'm looking in, because you never know when there might be hidden files. Built into some Linux distros are quick aliases you can use to speed things up. For example, in kali, you can type `ll`, and it corresponds to `ls -la`
#### bandit 4 -> 5
- 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
 - `file ./*`
 - `file ./-file*`
 - The file command will give you information about what the contents of a file are. Because of the dashes at the beginning of the filenames, you'll need to use the relative or absolute file paths again. The asterisk character is a wildcard, which means that it can substitute as any other character. We see that only 1 file has ASCII text (human readable). If you try to cat the non ASCII files, you'll see it's just gibberish.
#### bandit 5 -> 6
- HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
- `find -size 1033c`
- The find command has many options to filter out different types of files. Although bandit gives us 3 filters to look for, in this case, just the size one will do. The letter after the filesize, `c` in this case, determines what unit of size to use. 
	- `c` for bytes
	- `w` for 2 byte words
	- `k` for kibibytes (kibibyte=1024 bytes, kilobyte=1000 bytes)
	- `M` for mebibytes
	- etc.
#### bandit 6 -> 7
- morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
- `find / -size 33c -user bandit7 -group bandit6 2>/dev/null`
	- `/` -> start the search from the root directory
	- `-size 33c` -> file is 33 bytes in size
	- `-user bandit7` -> file is owned by bandit7 user
	- `-group bandit6` -> file is owned by bandit6 group
	- `2>/dev/null` -> redirect errors (2) to (>) the void (/dev/null)
- This is just an expansion on [bandit 5 -> 6](#bandit%205%20->%206) with more required tags and searching the entire computer instead of just 1 directory
#### bandit 7 -> 8
- dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
- `cat data.txt | grep millionth`
- `grep` searches for patterns in text, line-by-line. The challenge states that the word **millionth** is **next to** the password, which most likely means they're on the same line, so `grep` should work in this instance
#### bandit 8 -> 9
- 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
- `cat data.txt | sort | uniq -c | sort -nr`
- `cat data.txt` -> read the file and store it in standard output
- `sort` -> sort the standard output so all the duplicate lines are next to each other
- `uniq -c` -> count the occurrences of each line
- `sort -nr` -> sort the lines numerically in reverse order (lines with least duplicates will be shown first)
#### bandit 9 -> 10
- FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
* `strings data.txt | grep ==`
* `strings data.txt` -> only pulls ASCII text from a file, ignoring any binary gibberish
* `grep ==` -> looks for lines that start with at least 2 equals signs
* Now we're starting to get to the challenges where they can be completed in many different ways. Depending on your tool-set and knowledge, you may be able to find the answer in a much different way to how I found it
* Initially, I tried using `cat`, but `grep` gave an error, because it can't handle the binary data. That lead me to remembering the `strings` command, which is better suited for this challenge
#### bandit 10 -> 11
- dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
* `base64 -d data.txt`
* The challenge outright tells us that the file is encoded in base64, so after a little research on the `base64` command, we see that it can take a file or a string as input and you use the `-d` flag to decode.
* To learn more about base64, look into base2 (binary), base10 (decimal), base16 (hexadecimal), etc. What really helped me is learning the character set for each base
#### bandit 11 -> 12
- 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
- For this challenge, we'll move away from the terminal. We'll be using a browser-based tool called [CyberChef](https://gchq.github.io/CyberChef/). This tool is a necessity in this field, and I recommend you become very familiar with using it. It could've even been used to solve [bandit 10 -> 11](#bandit%2010%20->%2011)
- CyberChef uses **recipes** to build functions to modify text and files. Based on the challenge description, it seems like the text in `data.txt` has been passed through some sort of.... ***cipher***? Before moving on, look into rotating 13 position cipher
- Shift Cipher, Caesar Cipher, ROT13, etc. These are just a few of the many ciphers that you will most likely learn about in your career. If you look in CyberChef, you will find a **recipe** called ROT13. It rotates all the letters in the text by 13 positions (half the alphabet). Paste the original data.txt
#### bandit 12 -> 13 - FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
#### bandit 13 -> 14 - `ssh bandit.labs.overthewire.org -p 2220 -i sshkey.private -l bandit14`
#### bandit 14 -> 15 - 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
#### bandit 15 -> 16 - 
#### bandit 16 -> 17 - 
