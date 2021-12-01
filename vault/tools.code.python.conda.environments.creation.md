---
id: FARbP3EQoSJaBTcMcIXle
title: Creation
desc: ''
updated: 1638196629421
created: 1600970442296
stub: false
---


You can create an env from a given .yml file using 

```bash
conda env create -f environment.yml
```

Or directly like this 

```bash
conda create --name myenv
```

With a given python version 

```bash
conda create -n "myenv" python=3.6
```