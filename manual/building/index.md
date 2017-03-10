---
layout: default
title: Building
---

## Requirements

### Lua >= 5.1
Lsyncd depends on Lua 5.1 or greater; that is Lua 5.1, 5.2 or 5.3. For Lua versions beyond 5.1 you need an uptodate Lsnycd version. For most distributions you need to install the liblua??, the liblua??-dev and the lua?? package, with ?? being the respective Lua version.

### cmake >= 2.8

To configure Lsyncd to your system, cmake >= 2.8 is required

### rsync >= 3.1
During runtime Lsyncd needs rsync > 3.1 installed both on source and target systems.

## Compiling

With these requirements fulfilled building Lsyncd should be a straight forward process. Unpack the downloaded tar.gz file and run:

{% highlight shell %}
cmake .
make
sudo make install
{% endhighlight %}


###Install for Debian Jessie and Ubuntu Xenial from Source

The default install on Debian  and Ubuntu  works fine for clients, but not if you are running lsync as a server.

To ensure it works as a server on either of the above platforms, please proceed as follows:

{% highlight shell %}
Debian
apt-get source lsyncd
{% endhighlight %}

{% highlight shell %}
Ubuntu-
apt source lsyncd
{% endhighlight %}

You will now find a new subdirectory called lsyncd-version (eg. lsyncd-2.1.5)
cd into it and edit line 91 of default-rsyncssh.lua using your favourite editor.
Add a comma  at the end of line 91.
Save and close the file.

Then run these commands :

{% highlight shell %}
./configure
make
make install
{% endhighlight %}

If the ./configure fails, then run this :

{% highlight shell %}
Debian-
apt-get install liblua5.1-dev lua5.1 dpkg-dev automake rsync -y
{% endhighlight %}

{% highlight shell %}
Ubuntu-
apt install liblua5.1-dev lua5.1 dpkg-dev automake rsync -y
{% endhighlight %}

and run ./configure again.  If OK, please proceed with make and then make install.

To ensure the binary is in the Debian and Ubuntu PATH , please run these commands:

{% highlight shell %}
cd /usr/bin
ln -s /usr/local/bin/lsyncd lsyncd
{% endhighlight %}

It is now possible to invoke lsyncd as a server on Debian and Ubuntu. 
