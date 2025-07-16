# Docker Hacking Lab with The Damn Vulnerable Web Application

### To run the docker compose file
``` bash
    docker compose up -d
```

### Connect to the localhost port you set on line 15
``` bash
    localhost:3011
```

### Update & Upgade (In the Kali Container)
``` bash
    sudo apt update && apt upgrade -y
```
### Install Ping
``` bash
    sudo apt install iputils-ping -y
```

### Find the IP for the DVWA
```bash
    docker inspect network docker-security_lab__dvwa_hackinglab
```

- You can also find the IP from pinging the dvwa

``` bash 
        ping web-dvwa
```

### To end/bring down the containers
``` bash
    docker compose down -v
```