# How to install React and Maintain it.

## Instructions

![#](https://a.fsdn.com/allura/p/cmdrevd/icon)
This Icon means that you need to run a command to accomplish the described task!

Every step is described, but you have to use the [Cheat sheet](https://github.com/Tinker-Ware/blog-posts/blob/summerschool/2016/07/react_sysadmin_commands.md)
to find the command that best suits for the task you want to accomplish.

Feel free to ask your mentor anything.

This is a thinking exercise. Think, then act.

Read carefully this manual, think and then apply with commands.

Make sure you understand the task. That will make everything easier!

Good luck.


## VAGRANT CREATION

### Requirements

#### Virtualbox

[For Windows](http://download.virtualbox.org/virtualbox/5.1.0/VirtualBox-5.1.0-108711-Win.exe)

[For Linux](https://www.virtualbox.org/wiki/Linux_Downloads)

[For Mac](http://download.virtualbox.org/virtualbox/5.1.0/VirtualBox-5.1.0-108711-OSX.dmg)

#### Vagrant

[For windows](https://releases.hashicorp.com/vagrant/1.8.4/vagrant_1.8.4.msi)

[For Debian 32 bits](https://releases.hashicorp.com/vagrant/1.8.4/vagrant_1.8.4_i686.deb)

[For Debian 64 bits](https://releases.hashicorp.com/vagrant/1.8.4/vagrant_1.8.4_x86_64.deb)

[For Mac](https://releases.hashicorp.com/vagrant/1.8.4/vagrant_1.8.4.dmg)


Create a Folder to keep the files of this exercise.
Recommended: `~/Documents/tinkerware/deploy-exercise`

If you have git installed on your computer. Go inside your `deploy-exercise` folder
and clone the following repo: `https://github.com/Tinker-Ware/summerschool-infrastructure`

If you don't know what is git. Download the following file in your `deploy-exercise` folder:
`https://github.com/Tinker-Ware/summerschool-infrastructure/archive/master.zip`.

**Start using your Command line terminal from here.**

![](https://a.fsdn.com/allura/p/cmdrevd/icon) Go to the folder `deploy-exercise` and run `vagrant up` to start your machine.

Once it's done, run:

```
vagrant ssh
```

Welcome to your new fresh server.

If your want to know more details about Vagrant, you can visit
the [get started page](https://www.vagrantup.com/docs/getting-started/)

<!-- This will create a `Vagrantfile` wich contains the configurations for your local machine. -->
<!-- In this file, several options can be configured. Such as network configuration. -->
<!-- We will enable only local access to your machine. with the following line: -->

## SERVER CONFIGURATION

You should see something like this: (After `vagrant ssh`)

```
vagrant@tinkerware:~$
```

Now you're ready to start making some noise there.

The first thing a server needs is a group of users. You don't want everyone
going all over your servers, accessing everything, wrecking stuff and leaving
your servers vulnerable!

![](https://a.fsdn.com/allura/p/cmdrevd/icon) So first thing: Create a new user. Of course a user must belong to a group.
Go ahead and create a user called `intern1` that belongs to the group `sysadmin`

Now it is time to improve the security of the people accesing our servers.
For this, we need to update the ssh deamon to be more secure.

#### Edit SSH DEAMON
Edit `/etc/ssh/sshd_config`
You can use any editor you want. If you don't know which one to use, just run:
`sudo nano /etc/ssh/sshd_config`

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Add/edit the following lines:
```
PermitRootLogin no
PasswordAuthentication yes
Protocol 2
AllowUsers ${USER}
```

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Great. now create a secure password for new user and login to the new user
account.

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now that everything is set, we're ready to restart the ssh deamon.
`sudo service ssh restart`

As a good practice, one should normally set up the firewall as well, and
some other tasks in order to have a healthy and secure server, but we'll
leave that for another ocasion. Let's move to a deploy.

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now we need to install dependencies that our project needs, and some others
to download and manage files that are online.
`curl` is a great tool to download online resources.

React is a JavaScript library for building user interfaces and it's an
npm package. npm is the package manager for JavaScript.
Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.
Node.js uses an event-driven, non-blocking I/O model that makes it lightweight
and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of
open source libraries in the world.

![](https://a.fsdn.com/allura/p/cmdrevd/icon)In the npm documentation we can find te requirements to its installation.
In order for some npm packages to work (such as those that require building
from source), you will need to install the `build-essentials` package

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Add repository and install its signing key
curl -sL https://deb.nodesource.com/setup_4.x | bash -

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now, we have a serer ready to host a React project.
Let's get that project to run.

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now that it's there, we need to run the service to listen to requests
and show our project to the world. The necessary scripts can be found in
https://github.com/reactjs/react-tutorial.git

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now that we have all those files, in the README file are the steps
necessary to run the service. You can run it with node, since we prepared
the server for that.

Great!

Visit http://localhost:3000

And you should have a running instance of node!

Isn't it great to be a sysadmin? ... Now we need to fight with the developers
to run the code. haha....

... Next tutorial

First of all we need to fetch it from the repository on github.
But we can't clone it just anywhere.
The correct Path for this kind of projects would be `/opt`

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Lets create a folder there called `tinkerware_react` and
place the react project inside that path.



SUMMARY
---

1. Create vagrant
2. Login into vagrant machine
4. Update packages
5. Create users and groups.
6. Improve ssh security.
7. Install packages required to install node.
8. Install node dependencies
9. Install node.
10. Install react.
-- Start react server
11. Clone react server scripts
12. Run react server.
13. Visit http://localhost:3000
14. Be happy
--. Deploy our react code:
15. Create folder to contain code.
16. Clone page code in the folder.


Useful links
---

https://facebook.github.io/react/docs/getting-started.html

https://www.npmjs.com/package/react
https://github.com/reactjs/react-tutorial/
https://facebook.github.io/react/docs/tutorial.html
