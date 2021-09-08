---
id: w20rZxuoeHaxVvaZIFpYZ
title: Update
desc: ''
updated: 1609847515544
created: 1609689794407
---

To update a conda environment given a .yml file

https://stackoverflow.com/a/43873901

```bash
conda activate myenv
conda env update --file environment.yml
```

Or without the need to activate the environment (thanks @NumesSanguis):

```bash
conda env update --name myenv --file environment.yml
````
