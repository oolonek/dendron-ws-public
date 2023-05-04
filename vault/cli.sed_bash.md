---
id: QnOOo86260d85beTWwNIt
title: Sed_bash
desc: ''
updated: 1682950627290
created: 1609604978319
---

[[#oneday|tag.oneday]]
automate with a sed script ? the bib cleaning 

Some sed black magic 

```bash
echo "\{" | sed "s|\\\{|\\\'{|"
````
Double \\ to escape the \\

And repeat 

```bash
echo "\{jhdgjshgjhfsjdhgf\}" | sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g;"
````
Now add input and outputs 

```bash
sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g" library.bib > library_formatted.bib
```

We'll try to automatize the process using https://stackoverflow.com/a/13807906 fswatch and alternative to inotifywatch on linux https://linux.die.net/man/1/inotifywatch

So here is the small bash script. It will take the command line arg 1 and add the _formatted prefix to it. Could be cleaner and directly extract the filename to accomodate for various type of extension. Not the point here. If any body has an idea, please contribute ! :point_down: 


```bash
#!/bin/bash
sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g" "$1" > "${1%.bib}_formatted.bib"
```

```bash
#!/bin/bash

# fullfilename="$(basename $1)"
# extension="${fullfilename##*.}"
# filename="${fullfilename%.*}"

# echo $fullfilename
# echo $extension
# echo $filename

#echo "File added: " "$(basename $1)" "$(basename $1)"
sed "s|\\\{|\\\'{|g; s|\\\}|\\\'}|g" "$1" > "./formatted_bib/${filename}_formatted.bib"

````




fswatch has been somehow a nightmare to understand ...

to trouble shoot use the follwoing line to be sure of what exactly you take as input 

```bash
fswatch -0 ./mendeley_output/ | xargs -0 -n1 -I{} echo "{}"
```

## quick replace in text file

`sed -i 's/original/new/g' file.txt`

sed -i'' 's/CHARGE=1-/CHARGE=-1/g' /Users/pma/01_large_files/mgf/isdb_neg.mgf