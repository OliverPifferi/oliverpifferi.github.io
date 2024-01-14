---
layout: post
author: oliver
title: "How to install PHP 8.2 on Debian 11"
date: 2022-12-28
categories: [IT]
tags: [linux, software, opensource, foss, debian]     # TAG names should always be lowercase
image: '/images/debian_with_php.jpg'
---

## Although Debian is a modern Linux-distribution based upon stability, it sometimes misses actual packages like the latest PHP-iteration.

[Debian][1] 11, released on August 14th, 2021 with version 11.0, is more than one year available at the time of writing. The latest stable PHP-version, a foundation for many web services and use cases, is currently 8.2. After nearly one year, the latest PHP-iteration you can install on a modern Debian 11-system is still 7.4. While stability is - undoubtedly - still a key feature, the improvements from PHP 8.x are numerous with the factor „performance“ in the focus. This short but sweet tutorial shall show you how to safely install [PHP][2] 8.2 on a modern Debian-11-system.

By default, there is still a rational boundary for not always going with the latest versions of software packages. Anyway, depending on your own needs and used software, the change from PHP 7.4 to 8.x brings an enormous boost for all applications that rely on the latest PHP-version and have adopted their code to take advantage of the various improvements. Enabling our system to fetch the latest package is the key factor here and to gain this, we need to add the well-known repositories of [Ondřej Surý][3].

## Adding the repository

Ondřej Surý is the main Debian packager for PHP and other packages under DEB.SURY.ORG name you may already have encountered when venturing the web. As a service to the community he provides Ubuntu-PPAs for PHP, Apache2, nginx and others that are widely used. He also runs personal Debian packaging repository located at [https://packages.sury.org][4] and is told to be the best focal point for PHP-packages away from the standard.

On our Debian system, be sure that the „curl“ package is installed. If not, a 

	sudo apt install curl

does the trick before the command

	curl -sSL https://packages.sury.org/php/README.txt | sudo bash -x

will install the basic repository. On Ubuntu-systems, a

	sudo LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

takes care of the same effect.

To update all repositories and update some components, do a

	sudo apt update && sudo apt upgrade

to ensure your system is ready for all further installation tasks.

After having met all prerequisites, it’s now time to finally get familiar with PHP 8.2. To install the basic module, use the command

	sudo apt install php8.2-fpm

and, after conforming your choose, the FPM-version of PHP will be installed. To check whether you did succeed or not, a

	php -v

is always a good choice.

Further modules can be additionally installed depending upon your needs, for example the GD- and Curl-modules can be added via

	sudo apt install php8.2-gd php8.2-curl 

in no time!

## Verdict

With quite no efforts, we managed to install the latest iteration of PHP 8.x on our Debian 11-system. Further updates and security fixes will make use of the recently added repositories of Ondřej Surý. While the latest Ubuntu-version already brings PHP 8.2 from the scratch, older versions can also be equipped with this version by the alternative command above.

[1]:	https://www.debian.org/
[2]:	https://www.php.net/
[3]:	https://deb.sury.org/
[4]:	https://packages.sury.org