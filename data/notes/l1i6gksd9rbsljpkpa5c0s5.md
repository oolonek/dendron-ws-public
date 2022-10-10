
https://stackoverflow.com/a/7787159/4908629


❗ Mind were you are doing this ! It's not possible to go back :P 


for f in *; do mv "$f" "$f.tmp"; mv "$f.tmp" "`echo $f | tr "[:upper:]" "[:lower:]"`"; done



