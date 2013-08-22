---
layout: post
title: Installing Oracle Instant Client 11 on Mac OS X 10.8 (Mountain Lion)
time: 2013-08-22
---

I unfortunately need to work with Oracle software through work. For a long time, more than a year, Oracle hasn't provided any x86_64 binaries for Mac OS X, meaning neither Lion nor Mountain Lion has been supported. I personally use Mac OS X when developing but on our servers we use Linux distros so there we haven't had any problems. Being able to test things locally always make life a lot easier though, so today I decided to install some (*shuddering*) Oracle software in my dev environment again as Instant Client has now become compatible with the Lions.

We use Python a lot internally at work, and when extracting data from clients' databases we mostly use [SQLAlchemy](http://www.sqlalchemy.org/). SQLALchemy requires [cx_Oracle](http://cx-oracle.sourceforge.net/) for talking to Oracle databases, which in turn requires a number of packages to be installed. So the following had to be installed:

1. instantclient-basiclite-macos.x64-VERSION.zip
2. instantclient-sdk-macos.x64-VERSION.zip

They can be downloaded [here](http://www.oracle.com/technetwork/topics/intel-macsoft-096467.html).

In my example I installed version 11.2.0.3.0. Your `$INSTALL_PATH` might differ if you're not installing the same version.

{% highlight bash %}
$ BASE_PATH="/usr/local/lib/instantclient" && INSTALL_PATH="$BASE_PATH/instantclient_11_2"
$ mkdir -p $BASE_PATH
$ unzip /path/to/downloaded/instantclient-basiclite*.zip -d $BASE_PATH
$ unzip /path/to/downloaded/instantclient-sdk*.zip -d $BASE_PATH
$ echo "export ORACLE_HOME='$INSTALL_PATH'" >> ~/.profile
$ echo 'export DYLD_LIBRARY_PATH="$ORACLE_HOME:$DYLD_LIBRARY_PATH"' >> ~/.profile
# Reload this shell so that the new env variables are available.
$ ln -s $INSTALL_PATH/libclntsh.dylib.11.1 $INSTALL_PATH/libclntsh.dylib
$ exec $SHELL
# Now you should be able to just do:
$ pip install cx_Oracle
{% endhighlight %}
