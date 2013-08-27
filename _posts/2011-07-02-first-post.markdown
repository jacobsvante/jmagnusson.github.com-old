---
layout: post
title: First post
time: 2011-07-02 20:00:00
---

Finally got around to creating a blog. My primary goal with this blog is to write down lessons learned while programming that I think might be useful to me in the future. And hopefully some of you might find some goodies here too.
{% highlight python %}
class Pygments(object):
    """ <3 """
    def greet(self, obj):
        print 'Hello {}!'.format(obj)
p = Pygments()
for i in range(7):
    p.greet('World')
{% endhighlight %}