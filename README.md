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


**Start using your Command line terminal from here.**

BEFORE DOING ANYTHING
---

Go to the folder `deploy-exercise/summerschool-infrastructure` and edit the file `Vagrantfile`.
Find the line that contains `private_network` and change it for `public_network`. Delete the rest of the line (The `,ip: ip` stuff)
Replace the current Hostname of each machine to match the provided HOSTNAMES.

**My role:** | HOSTNAME in Vagrantifle
-------------|----------
If you're in charge of the react page(frontend) | `summerschool.react`
If you're in charge of the users microservice | `summerschool.users`
If you're in charge of the items microservice | `summerschool.items`
If you're in charge of the cart microservice | `summerschool.cart`


```
standard_machine config, summerschool.react', '192.168.33.100' # Replace the HOSTNAME.
config.vm.network :public_network ## CHANGE "private" for "public"
```

![](https://a.fsdn.com/allura/p/cmdrevd/icon) Go to the folder `deploy-exercise/summerschool-infrastructure` and run `vagrant up` to start your machine.

Once it's done, run:

Linux
---
From the terminal run:

```
vagrant ssh
```

Windows
---
Run [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

  - Hostname: 127.0.0.1
  - Login user: vagrant
  - login pass: vagrant


**Welcome to your new fresh server.**

If your want to know more details about Vagrant, you can visit
the [get started page](https://www.vagrantup.com/docs/getting-started/)


## SERVER CONFIGURATION

You should see something like this: (After `vagrant ssh`)

```
vagrant@tinkerware:~$
```

Now you're ready to start making some noise there.

The first thing a server needs is a group of users. You don't want everyone
going all over your servers, accessing everything, wrecking stuff and leaving
your servers vulnerable!

Run `sudo -i`

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
```

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now that everything is set, we're ready to restart the ssh deamon.
`sudo service ssh restart`

As a good practice, one should normally set up the firewall as well, and
some other tasks in order to have a healthy and secure server, but we'll
leave that for another ocasion. Let's move to a deploy.

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Great. now create a secure password for new user and login to the new user
account.

run `su - intern1`

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
from source), you will need to install the `build-essential` package

![](https://a.fsdn.com/allura/p/cmdrevd/icon)Add repository and install its signing key
curl -sL https://deb.nodesource.com/setup_4.x | bash -

Now we have the key to install nodejs. 
Install the package `nodejs`.

Now, we have a server ready to host a React project.
Let's get that project to run.

Now that it's there, we need to run the service to listen to requests
and show our project to the world.

![](https://a.fsdn.com/allura/p/cmdrevd/icon) (NO SUDO) Clone the repo you're supposed to run inside `/opt/summerschool/`

Probably you wont have permissions in that folder. fix it with `sudo chown -R intern1:intern1 /opt/summerschool`

- For the React page: https://github.com/Tinker-Ware/summerschool-frontend.git

- For the User microservice https://github.com/Tinker-Ware/summerschool-users-api.git

- For the Cart microservice https://github.com/Tinker-Ware/summerschool-cart-api.git

- For the Items microservice https://github.com/Tinker-Ware/summerschool-items-api.git


![](https://a.fsdn.com/allura/p/cmdrevd/icon)Now that we have all those files, in the README file are the steps
necessary to run the service. You can run it with `npm`, since we prepared
the server for that.

Great!

You should see now a message telling you that everything is running fine! 

And you should have a running instance of node!

Isn't it great to be a sysadmin? ... Now we need to fight with the developers
to run the code. haha....



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
