# [Level 0 → Level 1](https://overthewire.org/wargames/bandit/bandit1.html)
## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
## Solution
Use the SSH command to connect to port 2220 of Bandit with the -p flag, then enter the password provided earlier. Use the basic ls command to see if there are any files in the Bandit0 directory. Once you find the readme file, use the cat <file name> command to read the file and obtain the password.

Commands used: ssh, -p, ls, cat.
