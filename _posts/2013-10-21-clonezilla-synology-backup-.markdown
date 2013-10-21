--- 
layout: post 
title:  "Clonezilla meets Synology" 
date:   2013-10-20 23:24:45
categories: clonezilla synology 
---

Recently, I've had the pleasure of configuring a nice little NAS - Synology
DS1513+. At home, I run its smaller, two bay brother - the DS209, which had
served me well for the past few years, and I did not expect its bigger, badder
brother to disappoint. 

One of the primary motivators for acquiring the DS1513+ was the requirement for
cloning and backing-up entire hard-drive images over the network. Having some
experience with Clonezilla, I knew it to be a solid application, appropriate for
this job. I've used Clonezilla in the past to perform partition and complete
hard-drive image backups both locally, and over the network. The process was a
breeze, and I did not expect much resistance from DS1513+, however, I did end up
hitting a few snags along the way.

So here are some of the things to look out for if you happen to be dealing with
this beast:

1. **Make sure sshd is running.** 
It can be enabled through the admin web ui,
however, only `root` and `admin` users will be able to login. In order to enable
ssh login for other users, edit */etc/passwd* as the `root` user.

 E.g. change from: 

 `username:x:1030:100:UserName:/var/services/homes/username:/sbin/nologin` 

 to: 

 `username:x:1030:100:UserName:/var/services/homes/username:/bin/sh`

 and restart sshd:

 `/usr/syno/etc.defaults/rc.d/S95sshd.sh restart`


2. **Make sure SFTP is running.**
In order to save/restore an image to/from a remote location, Clonezilla will
mount the remote directory with SSHFS (SSH Filesystem). SSHFS operates via SFTP
and SSH, hence an ssh account with a home directory is needed on the NAS, and SFTP 
and SSH services have to be running. Both SSH and SFTP services can be enabled via the 
admin web ui. 

 It is important to note that Synology's SFTP service will convert the absolute path of
 the user's home (e.g. */volume1/homes/your_home_dir*) to */home*. This is
 something I did not anticipate, and it had caused me some grief as the remote
 directory would fail to mount.


