---
layout: post
title: Deploying Rails on Ruby 1.9
---
# Tools #

    * Ruby >= 1.9.1
    * Passenger >= 2.2.2
    * Rails >= 2.3
    * Mysql
    * Nginx (you'll compile one before we're done)

# Steps #

1) Install Ruby 1.9 (see instructions for your platform)

2) gem1.9 install passenger # Assuming your using a prefix, you dont have to

3) passenger-install-nginx-module

4) add the following to your nginx config before the last }
{% highlight bash %}
  server {
     listen 80;
     server_name www.yourhost.com;
     root /somewhere/public;   # <--- be sure to point to 'public'!
     passenger_enabled on;
  }
{% endhighlight %}

5) install mysql drivers
{% highlight bash %}
curl -O http://tmtm.org/downloads/mysql/ruby/mysql-ruby-2.8.1.tar.gz
tar zxfv mysql-ruby-2.8.1.tar.gz
cd mysql-ruby-2.8.1
ruby extconf.rb
make
sudo make install
{% endhighlight %}

6) sudo gem1.9 install rails

7) rails -d mysql somewhere

8) start nginx
