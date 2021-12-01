---
id: yWwGeUy7TlD8HLX74Kj1u
title: Activation
desc: ''
updated: 1638198351548
created: 1600970322838
stub: false
---


## Conda env activation 

source ~/anaconda3/etc/profile.d/conda.sh

conda activate my_env
conda activate opennbdb_dev_env


When this error occurs:

CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.
To initialize your shell, run

source ~/anaconda3/etc/profile.d/conda.sh


## ipykernel problems

pip install --upgrade pyzmq jupyterlab jupyter --force-reinstall

https://github.com/jupyter/notebook/issues/3435#issuecomment-566146547


