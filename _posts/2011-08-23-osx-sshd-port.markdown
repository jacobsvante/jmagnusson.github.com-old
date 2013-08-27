---
layout: post
title: Change ssh port in OS X Lion (and Snow Leopard)
time: 2011-07-02 20:00:00
---
You need to edit your ssh.plist launch daemon configuration file as follows:

{% highlight bash %}
sudo vim /System/Library/LaunchDaemons/ssh.plist

...

 17     <dict>
 18         <key>Listeners</key>
 19         <dict>
 20             <key>SockServiceName</key>
 21             <string>22</string> <-- REPLACE '22' WITH NEW PORT
 22             <key>Bonjour</key>
 23             <array>
 24                 <string>22</string> <-- REPLACE '22' WITH NEW PORT
 25                 <string>sftp-ssh</string>
 26             </array>
 27         </dict>
 28     </dict>

...

sudo launchctl unload -w /System/Library/LaunchDaemons/ssh.plist
sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist
{% endhighlight %}