---
id: IG6I7CXHNtcsZV3idu0Z8
title: Tar
desc: ''
updated: 1611406532608
created: 1609690553137
---


## tar command lines 

To create a tar.gz archive from a given folder you can use the following command. This will compress the contents of source-folder-name to a tar.gz 
archive named tar-archive-name.tar.gz

```bash
tar -zcvf tar-archive-name.tar.gz source-folder-name
```

To extract a tar.gz compressed archive you can use the following command

```bash
tar -zxvf tar-archive-name.tar.gz
```

If its a gzipped file

```bash
gzip -d tar-archive-name.tar.gz
```

This will extract the archive to the folder tar-archive-name.

To Preserve permissions

```bash
tar -pcvzf tar-archive-name.tar.gz source-folder-name
```

Switch the ‘c’ flag to an ‘x’ to extract (uncompress).

```bash
tar -pxvzf tar-archive-name.tar.gz
```


sudo certbot --authenticator standalone --installer nginx   -d directus.dbgi.org --pre-hook "service nginx stop" --post-hook "service nginx start"