## VAGRANT CREATION

### Requirements

#### Virtualbox
Donwload and Intall it.
https://www.virtualbox.org/wiki/Downloads

#### Vagrant

Install it
https://www.vagrantup.com/downloads.html

#### PuTTY (Windows Users)
http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html


### Download and run the proyect

Create a Folder to keep the files of this exercise.
Recommended: `~/Documents/summerschool/deploy-exercise`

Download and extract [this link](https://github.com/Tinker-Ware/summerschool-infrastructure/archive/master.zip) in that folder.
This is the [Github repo](https://github.com/Tinker-Ware/summerschool-infrastructure) if you want to clone it.

**Start using your Command line terminal from here.**

**Linux users**
Open your terminal and run `vagrant up` in the created folder.
```
$ cd Documents/summerschool/deploy-exercise/summerschool-infrastructure
$ vagrant up
```

**Windows users**
In windows, run `cmd`. (You can find it pressing Start button and searching for it)
Go to the path of the extracted/cloned project and run `vagrant up`.
```
> cd Documents\summerschool\deploy-exercise\summerschool-infrastructure
> vagrant up
```

Great! You should see this:
```
GATHERING FACTS *************************************************************** 
ok: [summerschool.react]

PLAY RECAP ******************************************************************** 
summerschool.react           : ok=1    changed=0    unreachable=0    failed=0  
```

If you achieved this, you're ready for tomorrow!
If not, try to fix any problem you may have or contact `hello@tinkerware.io`

Run `vagrant halt`.

Known issues
---

  - Make sure your Virtualbox version and Vagrant version are compatible.
  - Make sure you have Virtualization enabled from your BIOS
  - Make sure you enabled virtualization in your provider (if you virtualize on a virtualized machine)
