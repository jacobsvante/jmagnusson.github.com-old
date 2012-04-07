---
layout: post
title: Installing GraphicsMagick and pgmagick on OS X 10.7
time: 2012-04-08
---

After lots of trial and error I finally got pgmagick to install on OS X [thanks to okm's comment over @ stackoverflow](http://stackoverflow.com/questions/9786515/how-to-build-pgmagick-under-pythonbrew-on-os-x/9868631#9868631)

{% highlight bash %}
brew update
brew install boost graphicsmagick
ln -s /usr/local/lib/libboost_python-mt.a /usr/local/lib/libboost_python.a
pip install pgmagick
{% endhighlight %}
