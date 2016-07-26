Automate exercise with Ansible
---

In this exercise we need to modify several files.
Each one of them contains the necesary instructions of what to do there.

Modify them in the following order:

- Vagrantfile

**If you are in charge of the react page. (Frontend)**
- provisioning/roles/react_page/tasks/main.yml

**If you are in charge of any microservice (users/items/cart)**
- provisioning/roles/drakov/tasks/main.yml

- provisioning/site.yml

DONE!

Run your machine depending on the hostname of it.

Remember.

**My role:** | HOSTNAME in Vagrantfile
-------------|----------
If you're in charge of the react page(frontend) | `summerschool.react`
If you're in charge of the users microservice | `summerschool.users`
If you're in charge of the items microservice | `summerschool.items`
If you're in charge of the cart microservice | `summerschool.cart`

```
$ vagrant destroy -f
$ vagrant up summerschool.mymachine
```

There you go! Everything should be automatically installed.

Congrats!!!
