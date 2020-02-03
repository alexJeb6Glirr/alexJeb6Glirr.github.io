---
layout: post
title: Generate one big TSV file
subtitle:
tags: [homework]
comments: false
---

The code can also be found at <https://github.com/alexJeb6Glirr/python-scripts>.

After some modifications the extraction from Dispatch XML files into a single
TSV can be done as follows:


```shell
$ cd Homework
$ for f in $(ls -1 ../Dispatch); do python ../python-scripts/extract-from-xml.py ../Dispatch/$f; done
$ cat dispatch_186*tsv > the-whole-dispatch.tsv
$ ls -ls the-whole-dispatch.tsv
140M the-whole-dispatch.tsv
```

Assuming:

* the downloaded XML files are in the folder `Dispatch`
* the script is located in the folder `python-scripts` (on the same level)
* the result should be written into the folder `Homework` (on the same level)
