---
layout: post
author: oliver
title: "Installing the latest version of PostgreSQL on Ubuntu Linux"
date: 2021-11-02
categories: [IT]
tags: [linux, postgresql, database, software, ubuntu]     # TAG names should always be lowercase
image: '/images/photo-1629654297299-c8506221ca97.jpg'
---

## While Ubuntu Linux is — besides Debian — the Linux-distribution of my choice, some packages could be more up-to-date.

In this scenario given, my Ubuntu 20.04 doesn’t provide the latest PostgreSQL-version 14 which was released in late September. Working with v12 or v13 isn’t a real mud in the eye but the speed bump that comes with number 14 is quite impressive. In my case, a new installation was the base for a project and I decided to go with the latest release of PostgreSQL before doing anything else.

### About the repository

The way of adding the official repository is quite easy as PostgreSQL backs all [major distributions](https://www.postgresql.org/download/linux/) by its [PostgreSQL Apt Repository](https://apt.postgresql.org/). At the time of writing, the following versions of Ubuntu are maintained:

*   impish (21.10)
*   hirsute (21.04)
*   focal (20.04)
*   bionic (18.04)

So far, PostgreSQL gives its blessing for the following architectures:

*   amd64
*   arm64 (18.04 and newer; LTS releases only)
*   i386 (18.04 and older)
*   ppc64el (LTS releases only)

![](../images/1-zr9B0AyV4_Nq7bjLIZmFQQ.gif)

PostgreSQL — Logo

### Adding the latest repository

Three commands are necessary to add the specific repository to our distribution, a fourth command then installs the latest version — or the version you prefer.

First of all, we need to create the file repository’s configuration by typing

```
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
```


and importing the repository signing key afterwards:

```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```


![](../images/0-jIDnAj36B1SpN4od.jpg)

### Installation

Now update the package list just like you would do with any Ubuntu-/Debian-based distro:

```
sudo apt-get update
```


Then you need to choose whether to go with the latest version of PostgreSQL or choose a desired version, a command like

```
sudo apt-get -y install postgresql postgresql-contrib
```


for example will install version 14 at the time of writing and the contributing packages while

```
sudo apt-get -y install postgresql-12
```


will install version 12 in case you specifically need this iteration of PostgreSQL.

![](../images/0-8SulDl97TDV04HuQ.jpg)

### Conclusion

We managed to add the latest official PostgreSQL-repositories on — here — Ubuntu 20.04 in no time. Without any hassle we can now install the most up-to-date version of the modern PostgreSQL-relational database system. I hope this tutorial has helped you in your specific project.

And, by all means, don’t forget: You are now running an out-of-the-box configuration of PostgreSQL and there are many tweaks in the RDMS’s configuration file you may apply — but this is yet another story to be told! Making your configuration to suit your personal needs may be a quite demanding task but tools like [PGTune](https://pgtune.leopard.in.ua/) serve well here to adopt some parameters to your installation’s specific use case!