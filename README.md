﻿[![N|Solid](https://i1.wp.com/complemento.net.br/wp-content/uploads/2017/11/logo_otrs6free.png?fit=300%2C68&ssl=1)]()

Easy Docker Installation
========================

What's OTRS?
------------

OTRS is the world most popular Service Desk software, delivered by OTRS Group and a large opensource community. You can check more information and all OTRS Group Services in their web site:
http://www.otrs.com

This Docker image are maintained by Complemento, a Brazilian company dedicate to delivery ITSM with open source software. We develop many Free and Enterprise AddOns for OTRS. You can check our website for more information:
http://www.complemento.net.br

About this Image
----------------
This image aims to be a very easy way to get OTRS working, in a seconds. It includes all dependencies, Apache webserver and Mysql Server as well. It's indicated mainly for testing and educational purpose, since the idea behind Docker is to split all the components in several containers (Web server, Database etc).

If you are planning to use OTRS running on Docker in a production environment, then you should check the option bellow, that includes only the application in a container:
https://hub.docker.com/r/ligero/otrs/

How to Run it
-------------

 1. Install a docker server. You can download Docker Community Edition from this link: 

	https://www.docker.com/community-edition#/download

 2. Run the following command:

`docker run -ti --name easy_otrs -v otrs_mysql:/var/lib/mysql -v otrs_app:/opt/otrs -p 80:80 ligero/easy_otrs`

The container will start to load and when see the following lines, you will be able to access OTRS (the time should be different of course):
2017-11-30 01:48:52,119 INFO success: cron entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2017-11-30 01:48:52,120 INFO success: mysql entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
2017-11-30 01:48:52,120 INFO success: apache2 entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)

If you are not used to Docker, you can hit Ctrl+P+Q at this moment to get back to your system without interrupting the container execution.

Accessing your OTRS the first time
----------------------------------
If you are running docker in your localhost, just open your browser on:

**http://localhost/otrs/index.pl**
**user: root@localhost**
**password: complemento**

If you turned off your Docker or your computer
----------------------------------------------

In some situations, your OTRS container may be stopped or not. You can check it status by running:

`docker ps -a`

And see if the container easy_otrs (or wherever you have called it) is stopped or not.

If it's stopped, than you can start it again by running:

`docker start easy_otrs`

Additional parameters for the first run
---------------------------------------
If you are used to Docker, you optionally can define some parameters for the container creation:
- OTRS_DEFAULT_LANGUAGE: You can define the default language, such as pt_BR
- OTRS_FQDN: Define the hostname for all the notifications send from your system
- OTRS_SYSTEM_ID: Defines your OTRS System ID (Check OTRS Manual for more information)

