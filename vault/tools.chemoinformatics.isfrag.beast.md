---
id: Mlb5F1TDswu1OkB4yKCXI
title: Beast
desc: ''
updated: 1635414266944
created: 1634965352373
---

# Variant of the is fragmentation recipee on the beast

![[tools.chemoinformatics.isfrag]]


I launched too many job on the beast so at the end memory was full and all cores saturated.
Need to find a way to handle this.
I killed everything using 

sudo pkill cfm
sudo pkill docker


I will now need to list all calculated spectra

~/cfm/cfm_output$ ls > ../calculated_spectra.txt


I then fetch this back 
Or rather I will set up a connection to the beast via VSCode

We use sed line to remove the extensions 

sed 's|.log||g' calculated_spectra.txt

the -i operator allows to do it inplace

sed -i 's|.log||g' calculated_spectra.txt

I upload the full platinium to the beast 
rsync -rvz -e 'ssh' --progress ./platinum.tsv.gz allardpm@biolpc045600:/home/allardpm/cfm/

I run the 
frag_list_preparator_nb.py

gzip -d  sub_platinum_tofrag.tsv.gz



#####

messing around with gnu parralel

parallel -a names.txt echo
https://blog.ronin.cloud/gnu-parallel/



mv argument list too long 

find . -name . -o -type d -prune -o \
       -name '*.jpg' -o -name '*.png' -o -name '*.bmp' -o \
       -exec mv -t targetdir/ {} +

find Programs/cfm-id-code/cfm/bin/cfm_output/ \
       -name '*.log' -o \
       -exec mv -t cfm/cfm_output/ {} +


find ./cfm_output -name '*.log' -exec mv {} . \;