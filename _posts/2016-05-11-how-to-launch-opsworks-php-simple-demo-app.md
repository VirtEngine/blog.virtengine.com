---
title: How to launch PHP - OpsWorks   in VirtEngine
layout: post
og_image_url: "https://blog.virtengine.com/res/gotalk-intro.png"
description: How to launch PHP - OpsWorks   in VirtEngine
---

### Introduction
AWS OpsWorks PHP is a simple demo app that can help you get started using your favourite PHP language.

This tutorial will guide you in launching a php web application (OpsWorks) in VirtEngine.

<a href="https://console.VirtEngine.com" target="_blank">
 

### Prerequisites
* You are running Ubuntu 14.04 or Linux workstation.

* Git installed on your workstation, which you can do by following the [How To Install Git with Apt.](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04)

* You have an account on GitHub, which is a Git repository host.

* You have to create a valid credential for accessing https://console.VirtEngine.com. [How to create an account with VirtEngine](https://blog.virtengine.com/2016/05/27/how-to-launch-ubuntu/)

* You have to install openssh-server for ssh access.

		sudo apt-get install openssh-server

* Check SSH working properly

		ps aux | grep sshd

This initial section contains everything you need to get OpsWorks PHP Simple Demo App and running on your server.

### Step-1 Fork OpsWorks PHP Simple Demo App
* Fork Open OpsWorks PHP Simple Demo App
from https://github.com/verticeapps/php_simpleapp.git

* You will be see the fork option in the top right corner of the git hub page.click the fork option.

* The OpsWorks PHP Simple Demo App repository is forked into your git repository.

### Step-2 Launch the app
1. Go to VirtEngine Dashboard

2. Click Marketplace on the top bar.Marketplace contains all the linux distros, applications, services and microservices which VirtEngine supports.

4. Click PHP Icon.A window will pop up for your repository selection.

3. Pick a repository by choosing your git repository.

  Let us use Github: < mygithub >/php_simpleapp.git

5. You can create new sshkey or use an existing sshkey or upload your own sshkeys too.

6. To launch PHP App.Click Create.

* Voila ! Your App is up to date.

* Now that you have launched your app, you might want to launch a service (database) and bind it

### **Buildpack for php**

We use a PHP build pack using our super cool chef-repo.

The buildpack for PHP

	#!/bin/bash
	#Php builder
	#megam_php
	local_repo=/var/www/html/currentremote_repo=https://github.com/megamsys/opsworks-demo-php-simple-app.git
	megam_home=/var/lib/megam/gulp
	filename=$(basename "$remote_repo")
	extension="${filename##*.}"
	project="${filename%.*}"
	cd $megam_home
	rm -r $project
    git clone $remote_repo
    rm -r $local_repo/*
    mv ./$project/* $local_repo
    cd $project
    if [  -f "./$project/start" ]; then
    chmod 755 ./$project/start
    ./$project/star
    fi
    service apache2 restart



### **Step-3 Open Your Web browser**
You can access your web page using https://IP_ADDRESS/current


{<1>}![](https://blog.virtengine.com/content/images/2016/05/ops.png)

### Conclusion

These are the very simple steps to launch a php web app (OpsWorks PHP Simple Demo App) using github repository.

###Deploy PHP app now
<a href="https://console.VirtEngine.com" target="_blank">
 
