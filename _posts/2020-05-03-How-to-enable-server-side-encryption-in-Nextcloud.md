---
layout: post
author: oliver
title: "How to enable server-side encryption in Nextcloud"
date: 2020-05-03
categories: [IT]
tags: [nextcloud, foss, software, cloud, privatecloud, europe, digitalsovereignty]     # TAG names should always be lowercase
image: '/images/Nextcloud_Hub.jpg'
---

# When it comes to your private-hosted cloud, Nextcloud is surely one of the solutions to get this task accomplished.

Hosting your data in a local datacenter or on a small box at home the data sovereignty of your files is within your hands is no problem with this piece of software. While Nextcloud is quite easy to install and maintain, you might think about enforcing the level of security within your private cloud so have you ever thought of enabling the server-side encryption in Nextcloud so far? If not, let me show you how this may be accomplished!

After you have made the move from a comfortable and public cloud provider to your own solution, you will get quite familiar with the new environment quite fast. But did you ever think of locking down the files on your own Nextcloud-instance directly on the servers? While you surely use some external security features like a firewall to protect the machine behind the private cloud, encrypting the files on the server’s side should be one of your additional (and golden) thoughts for completing the vision of private cloud security.

By default, the server-side encryption is disabled in your standard Nextcloud-installation and there are reasons for that. But, by all means, theoretically the provider hosting your VPS could have access to the machine’s file-system where all your files are stored — without encryption. Out-of-the-box Nextcloud encrypts remote data but the files are stored without encryption on the file system. The possibility of accessing these files without your knowledge is — of course — just an on-paper assumption but should be considered in your plannings as long as you don’t have physical access to your private cloud solution. Fortunately, the folks at [Nextcloud](https://nextcloud.com) made it still easy for you to get rid of this potential problem.

![](../images/1-3MxP2HBeglCk--kbnyBXpQ.jpg)

Besides the good, there are also some aspects you should know about when enabling the feature of server-side encryption: On the one hand, the file size may increase up to 35% and still, there is no full guarantee for security at all as security is (of course) more than just this feature. All future files uploaded to the server will be encrypted from the point of upload unless you decide to encrypt the rest by using the command line in connection with the „**occ**“-command (which we will do afterwards). Last but not least take care of the recovery keys and of a frequent backup as we are just shifting up the level of security — so (like in every situation) I recommend to backup early and to backup often!

To get the process running at last, access your Nextcloud-dashboard as the Admin-User or a user with administrative rights. Navigate to the app-section and check the disabled apps where you will find the „**Default encryption module**“. Enable the app.

![](../images/1-w0_v-dXvQyX7z0SWnpepXA.jpg)

Now head to „**Privacy**“ in your Nextcloud-settings and enable the server-side encryption. Note: Once you have enabled this feature, you cannot disable it by the web interface. The process will start once you log out and log in again, finally enabling the feature. For you, this means you must ensure that users’ encryption keys are regularly backed up. If an encryption key is lost for whatever reason, the specific user’s data cannot be accessed anymore!

As for the keys (and for your convenience) these are stored in specific locations of your Nextcloud-data directory. While the individual user keys are stored in the „files\\\_encryption“-location in the particular user folder, all other keys remain in the root of your Nextcloud-data directory, more precisely in the “files\\\_encryption“-folder therein. While mine is located in “/var/nextcloud\_data“, yours may be different, especially when sticking to the standard of „/var/www/nextcloud/data“ which is the default.

So we finally managed to enable the Server-side encryption on our Nextcloud-instance for the files yet to come. But what if we want to encrypt the files which are already stored in our private cloud? This can be done as well — of course — but beware that this may take some time depending on the specs your system is running with as well as on the amount of data you have placed in your Nextcloud so far. To accomplish this, simply enter the shell of the Linux-machine hosting your Nextcloud and head to the /var/www/nextcloud-directory.

Now we must use the command

> sudo -u www-data ./occ encryption:encrypt-all

to get this process running. Check the last warning (and understand the consequences) and if everything is okay, hit the “Y”-key to start to process of encrypting the existing files of all users within your Nextcloud-instance. The master key will be used to encrypt all files and you should see the progress until occ tells you that everything has been encrypted successfully. As stated before, this may take some time according to the data stored in your Nextcloud and the hardware specifications of the machine hosting it.

Should you, by the way, ever be in the need of disabling encryption (for whatever reason), you may do so by typing

> sudo -u www-data ./occ encryption:disable

straight from your Nextcloud-root.

Last but not least we have used another tool that the people at Nextcloud have implemented in their great solution. Just like every tool it needs a certain way of using it — putting a nail in a wall with the shaft of a hammer won’t succeed — but if you take care of the encryption, you should also take care of other things: Amongst them surely monitoring your private cloud, checking for irregular accesses or behaviors, and — mainly — the backup-thing. Paired with sticking to the latest updates and security fixes of the used software as well as of the OS being a foundation for everything placed on it, you should be quite safe!