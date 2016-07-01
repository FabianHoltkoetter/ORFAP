---
title:  'Technical Installation Guide'
author:
  - ORFAP
  - Organisation for all purposes
lang: de
geometry: [top=1.25cm, bottom=1.25cm, left=2cm, right=1.25cm]
documentclass: scrartcl
---
# Installation Guide
## Server Side Installation

To deploy the application on your companies server you need to install docker on the server you want to deploy the application on. A docker installation guide can be found
`https://docs.docker.com/linux/`.

Further you need to make sure you have a MYSQL-Database setup with the following data:
* Username: ExtDev2
* Password: ***

To setup a MYSQL-Database on the server please refer to
`http://dev.mysql.com/doc/refman/5.7/en/linux-installation.html`.

Now you are ready to go to get the application up and running! From here it is as simple as executing some commands.

* Starting the Backend:
`docker run -d -e TZ=GMT+2 -e "SPRING_PROFILES_ACTIVE=production" -p 8081:8080 darenegade/fapbackend`
* Starting the Crawler:
`sudo docker run -d -p 8082:8081 arne2/fapcrawler`
* Starting the GUI:
`sudo docker run -d -p 8080:80 petermueller/flight-analyzer`
* Starting the API-Gateway:
`sudo docker run -d -p 80:8080 darenegade/fapapigateway `

If you want you can also start the so called Watchtower. This docker container will keep all parts of the applications updated automatically when a new version is released.

* Starting the watchtower:
`sudo docker run -d -v /var/run/docker.sock:/var/run/docker.sock centurylink/watchtower`

Some more neat commands to get you started with using docker:

* `sudo docker ps` lists all running containers. The `-a` flag lists all stopped containers, too.
* `sudo docker logs <id>` shows the log output of this container. `-f` tails the log so you can continue watching the output.
* `sudo docker stop <id(s)>` stops all given containers.
* `sudo docker stats <id(s)>` show the current system usage of all given containers.

Now just wait for all containers to start and you can continue by crawling your first data. How to do this? Just follow the user documentation!

## Client Side Installation

To get the application running on your machine you only need two things.

1. You need a connection to your companies network. You can connect to your companies network with the companies VPN.
You can find an instruction how to connect to it `https://www.lrz.de/services/netz/mobil/vpn_en/`

2. A modern web browser. It doesn't matter if it's Firefox, Chrome or Microsoft Edge. Only Internet Explorer is not supported.

Now you are ready to go! Just go to 10.28.2.166 and login with your name. For further instruction on how to use the application please refer to the user guide.
