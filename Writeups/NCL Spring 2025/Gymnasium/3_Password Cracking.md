### TIP: Install password cracking tool on host machine to speed up cracking

https://hashes.com/en/decrypt/hash
#### Rockyou
* I used hashcat with the rockyou.txt wordlist
* `hashcat <hashfile>` to find what mode to use
* `hashcat -m <mode> <hashfile> <wordlist>`
* `hashcat -m 0 hashes.txt rockyou.txt`

#### Mask
* You can use custom character sets in hashcat if you know the format of the password
* `hashcat -m 0 hashes.txt -a3 SKY-HQNT-?d?d?d?d`
	* ?l = abcdefghijklmnopqrstuvwxyz
	* ?u = ABCDEFGHIJKLMNOPQRSTUVWXYZ
	* ?d = 0123456789
	* ?h = 0123456789abcdef
	* ?H = 0123456789ABCDEF
	* ?s = «space»!"#$%&'()+,-./:;<=>?@\]^_{|}~
	* ?a = ?l?u?d?s
	* ?b = 0x00 - 0xff

#### Law & Order
* The challenge with this one is finding a good wordlist and using the hybrid wordlist + mask attack mode
* When searching for wordlists, try searching specifically for github sites
* `hashcat -m 0 hashes.txt svu.txt -a6 ?d?d`

#### Kali Linux (cracking /etc/shadow)
```
hollie:$y$j9T$/WzixhAsn8sdXhCquYzh01$KZlio78LilItobsx/17ecFf1e2SbsduhP1sZEWuHrL4:18934:0:99999:7:::
```
* Username - `hollie`
* Hash Method - `$y$j9T$` (yescrypt)
* Salt - `/WzixhAsn8sdXhCquYzh01`
* Hash -`KZlio78LilItobsx/17ecFf1e2SbsduhP1sZEWuHrL4`
* Last Password Change - 18934 (unix time, days since Jan 1st, 1970)
* Minimum Days Required Between Password Changes - 0
* Maximum Days Password is Valid - 99999
* Number of Days Before User is Warned - 7

[4\_Forensics](4_Forensics.md)