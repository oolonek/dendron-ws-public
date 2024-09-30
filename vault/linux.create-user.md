---
id: odldFcVy0q1pW8lql76Jm
title: Create User
desc: ''
updated: 1726822782359
created: 1638267558093
---
# User creation on a linux server


Following these instructions 

https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/



# RHEL

https://linuxconcept.com/how-to-create-a-sudo-user-on-rhel-red-hat-enterprise-linux-operating-system/

adduser user_name
passwd user_name



sudo useradd -m jane

sudo passwd jane



```bash
sudo usermod -aG docker $USER
```

You can check whether your user has been added to the `docker` group by running the following command:

```bash
groups $USER
```


