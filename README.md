<h1>Linux Forensics</h1>

<h2>Description</h2>
In this lab, we will touch on the following items regarding Linux forensics:

- <b>Finding OS, account, and system Information on a Linux machine</b>
- <b>Finding information about running processes, executed processes, and processes that are scheduled to run</b>
- <b>Finding system log files and identifying information from them</b>
- <b>Common third-party applications used in Linux and their logs</b>
<br />


<h2>Languages and Utilities Used</h2>

- <b>Linux Terminal</b>
- <b>Linux CLI</b>

<h2>Environments Used </h2>

- <b>Linux Virtual Machine</b>

<h2>Lab Walk-through</h2>

<p align="center">
1. To find the OS release information we can use the ‘cat’ command to read the file located in /etc/os-release. <br/>
<img src="https://imgur.com/dbO7vSk.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
<br />
<br />
2. The /etc/passwd file contains information about all the user accounts that exist on the system. You can use a column -t -s : command to make it easier to read. This will then list all the users. The password information field will show a ‘x’ to signify that it is in the /etc/shadow file. <br/>
<img src="https://imgur.com/y9KD7va.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
<br />
<br />
3. The group information will be stored in /etc/group.<br/>
<img src="https://imgur.com/uyMit1a.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
<br />
<br />
4. The users who are allowed to elevate their privileges to sudo are stored in the /etc/sudoers file.:  <br/>
<img src="https://imgur.com/YCRkKyo.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
5. In the /var/log directory we can see log files of all kinds. The btmp file saves information about failed logins, and the wtmp keeps historical data about logins. These are binary files and you can not use the cat command to read these, instead using the ‘last’ command will allow you to see these logs <br/>
<img src="https://imgur.com/aRrOceW.png" height="80%" width="80%" alt="Splunk Searching Steps"/><br />
<br />
6. Every user that authenticates on a linux host is logged in the auth log. This is located in /var/log/auth.log. Since this a fairly large file we can use the commands tail, head, more or less to make it easier to read  <br/>
<img src="https://imgur.com/RGPJNJA.png" height="80%" width="80%" alt="Splunk Searching Steps"/><br />
<br />
7. The hostname is stored in the /etc/hostname directory.  <br/>
<img src="https://imgur.com/o0itvQs.png" height="80%" width="80%" alt="Splunk Searching Steps"/><br />
<br />
8. Timezone information can be a significant piece of information, as this can tell us the general location and time window it might be used in. This can be found it the /etc/timezone directory.  <br/>
<img src="https://imgur.com/6tCBcEC.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
9. To find information about the network interface we can read the /etc/network/interfaces directory.   <br/>
<img src="https://imgur.com/o0kbTUY.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
10. The IP command can help us find information about the mac and IP of different interfaces  <br/>
<img src="https://imgur.com/katVoDg.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
11. The netstat command will show active connections on a linux host.  <br/>
<img src="https://imgur.com/OOObWGB.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
12. The ‘ps’ command will show all the running processes on a system.   <br/>
<img src="https://imgur.com/t9ttEYo.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
13. The file /etc/hosts contains the DNS name assignment.  <br/>
<img src="https://imgur.com/7IOOkdk.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
14. The information about DNS servers that a Linux host talks to for DNS resolution is stored in the /etc/resolv.conf file.  <br/>
<img src="https://imgur.com/amu9gBT.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
15. Cron jobs are commands that run periodically after a set amount of time.  A Linux host maintains a list of all these cron jobs located in a file at /etc/crontab.  <br/>
<img src="https://imgur.com/mphHMvp.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
16. Like windows, services can be set up to run in the background after every system boot. A list of these services are stored in the /etc/init.d directory. We can check the contents using the ls command. <br/>
<img src="https://imgur.com/VYwfJQv.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
17. When bash shell is spawned, it runs the commands stored in the .bashrc file. This can be considered a startup list of actions to be performed. Hence it is a good place to look for persistence.  <br/>
<img src="https://imgur.com/KeWe4jh.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
18. All the commands that are run on a linux host using sudo are stored in the auth log. We can use the grep command to filter out only what we need.  <br/>
<img src="https://imgur.com/tpTfSxM.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
19. Any commands other than the ones using sudo are stored in the bash history. Every user’s bash history is stored separately in that user’s home folder. When examining bash history we would have to look at every users history, including root.  <br/>
<img src="https://imgur.com/PUZF9A8.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
20. The Vim text editor stores logs for opened files in vim in the file name .viminfo in the home directory. This file contains command line history, search string history, etc. for opened files. <br/>
<img src="https://imgur.com/Wyyying.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
21. The Syslog contains messages that are recorded by the host about system activity. The detail which is recorded is configured through the logging level.   <br/>
<img src="https://imgur.com/MaU0f4z.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
22. We have already discussed the Auth logs earlier. The Auth logs contain information about users and authentication-related logs. <br/>
<img src="https://imgur.com/LHESzTA.png" height="80%" width="80%" alt="Splunk Searching Steps"/>
 <br />
<br />
23. 23.	Third party logs are stored in the /var/log directory along with the other logs.  <br/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
