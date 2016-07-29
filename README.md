Automate exercise with Ansible
---

In this exercise we need to modify several files.
Each one of them contains the necesary instructions of what to do there.

Modify them in the following order:

**If you are in charge of the react page. (Frontend)**
- provisioning/roles/react_page/tasks/main.yml

**If you are in charge of any microservice (users/items/cart)**
- provisioning/roles/drakov/tasks/main.yml

___


- provisioning/site.yml

- provisioning/hosts

CHECK:

- provisioning/host_vars/summerschool.react

DONE!

Run your machine depending on the hostname of it.

Remember.

```
$ vagrant destroy -f
$ vagrant up
```

There you go! Everything should be automatically installed.

Congrats!!!
