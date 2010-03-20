---
layout: post
title: Installing on Ubuntu
---
# Using Synaptic #

*warning: it appears that the Ubuntu package is currently 1.9.0, which you don't want*

Ruby 1.9 is available via the Synaptic installer.  Be sure to select ruby1.9, irb1.9 and rubygems1.9
From Source

{% highlight bash %}
  sudo apt-get -y install libc6-dev libssl-dev make build-essential libssl-dev libreadline5-dev zlib1g-dev
  tar zxfv ruby-1.9.1-p0.tgz
  cd ruby-1.9.1-p0
  ./configure
  make
  sudo make install
{% endhighlight %}

