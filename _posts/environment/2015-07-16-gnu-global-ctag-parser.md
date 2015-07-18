---
layout: page
title:  "GNU global configuration use ctags parser"
breadcrumb: true
categories:
    - environment
comments: true
show_meta: true

---



~~~
# Installation of GLOBAL
# It assumed that ctags command is installed in '/usr/local/bin'.
$ ./configure --with-exuberant-ctags=/usr/local/bin/ctags
$ make
$ sudo make install

# Executing of gtags
# It assumed that GLOBAL is installed in '/usr/local'.
$ export GTAGSCONF=/usr/local/share/gtags/gtags.conf
$ export GTAGSLABEL=ctags
$ gtags                         # gtags invokes Exuberant Ctags internally
~~~

<a>http://www.gnu.org/software/global/manual/global.html </a>
