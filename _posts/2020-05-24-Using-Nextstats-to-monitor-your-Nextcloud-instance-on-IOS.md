---
layout: post
author: oliver
title: "Using Nextstats to monitor your Nextcloud-instance on iOS"
date: 2020-05-24
categories: [Thoughts]
tags: [nextcloud, software, apple, linux, ios, mobile]     # TAG names should always be lowercase
image: '/images/photo-1545665277-5937489579f2.jpg'
---

## „There’s an app for that“ is one of the famous slogans we know in this age of apps. Sometimes it just needs a good idea (and the skill of coding though!) to build an application for a mobile device.

One of those examples Is „Nextstats“ which simply beams the essential information on your Nextcloud’s system environment on your iOS device. That is quite easy to accomplish — thanks to developer Jon Alanis — so let me show you how!

![](../images/1-SMWW_epmjuL7oqluNuomxA.jpg)

First of all there is the download in Apple’s App Store. After the first start you’ll find an empty screen so feel free to add your Nextcloud-server to the dashboard by using the „+“-button.

![](../images/1-AD4sJ78wOihIf1Q5TBIcQQ.jpg)

The process is self-explaining: Give your server an optional nickname, add the server URL (currently only SSL-encrypted installations from v15 on) and you may connect.

![](../images/1-d2t4nETl6a2ZIoQdHWZrOg.jpg)

Now you need to grant the app access to your Nextcloud. A standard user won’t work and doesn’t seem to redeem the token so you need to connect your Nextcloud with admin-credentials.

![](../images/1-gMq35yuOUSTsYELhPRJmSw.jpg)

Once this has happened, you will the the dashboard with your recently-added instance which should show up with the „online“-status.

![](../images/1-XM8ebUgAZrbING3WndlT5Q.jpg)

A click on it will reveal the system stats and other useful information about your storage, your Webserver and PHP-version as well as the database backing your instance. Other pieces of information join so there are plenty of entries for you to see which seem to have been pulled from Nextcloud’s „System“-pane.

![](../images/1-15xn0SdHv3kz4qg-bsyz_Q.jpg)

I found myself searching for a way to monitor my Nextcloud instance as well as my customer’s installations so this app surely fills up a gap. It is quite new but exactly does what it promises and works without any hassle once you use administrative credentials during the setup. As I wrote at the beginning it sometimes just needs a good idea to come up with an app many people may strive for — Nextstats is one among those so feel free to try it!