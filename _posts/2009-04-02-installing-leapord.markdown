---
layout: post
title: Installing Ruby 1.9 on OS X Leopard
---
# Pre Reqs #
You need XCode 3.1 or greater to install Ruby 1.9.1 

# MacPorts #
Personally I've found using a package manager is much simpler that trying to roll you own of everything.  One of the reasons this works so well for me is that I know when to give up and compile my own package.  Ruby 1.9 is in [MacPorts](http://macports.org), it is stable and that is how I install on Ruby 1.9 on the vast majority of my Macs (there are 4 that I maintain btw).

{% highlight bash %}
  sudo port install ruby19 +mactk +c_api_docs
{% endhighlight %}

## Variations ##
MacPorts has the concept of variants which are the options for your package.  According to the command "port variants ruby19" there are the following availible:

{% highlight bash %}
  ruby19 has the variants:
      nosuffix: Don't add the 1.9 program suffix to the executables. Note: that makes the port conflict with ruby (1.8), rb-rubygems, and rb-rake ports
      c_api_docs: Generate documentation for Ruby C API
      tk: Build using MacPorts Tk
      mactk: Build using MacOS X Tk Framework
      universal: Build for multiple architectures
{% endhighlight %}

As you can see I like having the C API docs and using the existing MacTK framework.

# By Hand #
Maybe MacPorts makes you angry, you've had bad luck with it in the past or you just want to compile your own.  This is a totally legitimate thing to want to do.  It turns out its not hard either (knock on wood)

{% highlight bash %}
  curl -O ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.1-p0.tar.gz
  tar zxfv ruby-1.9.1-p0.tar.gz
  cd ruby-1.9.1-p0
  ./configure --enable-shared --enable-pthread CFLAGS=-D_XOPEN_SOURCE=1
  make
  sudo make install
  echo 'export PATH="/usr/local/bin:/usr/local/sbin:/usr/local/mysql/bin:$PATH"' > ~/.profile
  source ~/.profile
  ruby -v
  ruby -e "puts 'hello world'"
{% endhighlight %}

I did an install this way a few days ago.  If you get stuck checkout this [Gnu Screen log](/files/screenlog.0) of the install, it may help you
