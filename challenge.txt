Bandit Writeup 🚀
Welcome to my Bandit challenges writeup! Below, I’ve documented my solutions, commands, and key takeaways for each level. Let’s dive into the details! 💻

Challenge no       : 01
Challenge level   : bandit 4 → 5 
Problem              : Find ASCII type file among many files from a folder 
Commands Used:
I. cd inhere
II. file <file name> ( here “data” means hex code)
III. find /path/to/folder -type f -exec file {} \; | grep ASCII
Password for next level: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

Challenge no.   : 02
Challenge Level : Bandit 6 → 7
Problem         : Find a specific file owned by a            specific user and a group and have specific size among many files from “/” or root directory.
Commands used   :
I. find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
My problem      : I saw a huge permission denied lists, to redirect that error I used “2>/dev/null”.
Key takeaway    : The "2>/dev/null" command is used to redirect error messages (stderr) to /dev/null, which effectively discards them so they don't appear in the output.
Password        :morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj


Challenge no.   :03
Challenge level :Bandit 8 → 9
Problem         :The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
Commands used   : 
 I. cat data.txt | sort | uniq -u
Key takeaway    : sort — rearranges lines so identical words are consecutive. uniq -u — prints only lines that occur exactly once. 
Without sort, uniq -u would miss duplicates that aren’t next to each other.Piping “|” in Linux is used to connect the output of one command directly to the input of another, allowing users to process data efficiently without needing to create intermediate files.


Challenge no.   :04
Challenge level :Bandit 10 → 11
Problem         : decode a base64 text in terminal.
Commands used   :
I. echo "<encoded code>" | base64 --decode
key takeaway    :Base64 can be decoded because it is a reversible encoding method that converts binary data into a text format using a specific set of 64 printable characters. This allows the original binary data to be reconstructed from the encoded string by reversing the encoding process, which involves mapping the characters back to their corresponding binary values.

---

## **Challenge 06** 🎯  
**Level:** Bandit 12 → 13  
**Problem:** The password for the next level is stored in a compressed file named `data.txt`.  
**Solution:**  
I decompressed the file using a series of commands: `xxd`, `mv`, `gzip`, `bzip2`, and `tar`.  

**Commands Used:**
1.xxd -r data.txt > data 
2.mv data data.gz 
3.gzip -d data.gz 
4.mv data data.bz2 
5.bzip2 -d data.bz2 
6.tar -xf data.tar 

**Key Takeaway:**  
Understanding file compression formats and how to decompress them is essential. The `xxd` command is used to reverse a hex dump, and `gzip`, `bzip2`, and `tar` are used for decompression.  


---

## **Challenge 07** 🎯  
**Level:** Bandit 13 → 14  
**Problem:** The password for the next level is stored in `/etc/bandit_pass/bandit14` and can only be read by user `bandit14`.  
**Solution:**  
I used `ssh` to connect to the next level and read the password file.  

**Commands Used:**
1.ssh bandit14@localhost 
2.cat /etc/banditpass/bandit14 

**Key Takeaway:**  
The `/etc/bandit_pass` directory contains passwords for each level, but they can only be accessed by the respective user.  


---

## **Challenge 08** 🎯  
**Level:** Bandit 14 → 15  
**Problem:** Submit the password of the current level to port 30000 on localhost.  
**Solution:**  
I used `nc` (Netcat) to send the password to the specified port.  

**Commands Used:**
1.echo "Password" | nc localhost 30000 

**Key Takeaway:**  
Netcat (`nc`) is a versatile tool for networking tasks, such as sending data to a specific port.  


---






## **Challenge 09** 🎯  
**Level:** Bandit 15 → 16  
**Problem:** Submit the password of the current level to port 30001 on localhost using SSL encryption.  
**Solution:**  
I used `openssl s_client` to establish an SSL connection and send the password.  

**Commands Used:**
1.openssl s_client -connect localhost:30001 

**Key Takeaway:**  
SSL encryption ensures secure communication. The `openssl s_client` command is used to connect to SSL-enabled services.  


---

## **Challenge 10** 🎯  
**Level:** Bandit 16 → 17  
**Problem:** The password for the next level is stored in a file located somewhere on the server and is accessible via a port between 31000 and 32000.  
**Solution:**  
I scanned the ports using `nmap` and found an SSL-enabled port. Then, I used `openssl s_client` to retrieve the password.  

**Commands Used:**
1.nmap -p 31000-32000 localhost 
2.openssl s_client -connect localhost:31790 

**Key Takeaway:**  
Port scanning with `nmap` helps identify open ports, and `openssl s_client` is used for SSL connections.  

