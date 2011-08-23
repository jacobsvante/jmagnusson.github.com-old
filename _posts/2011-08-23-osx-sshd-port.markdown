---
layout: post
title: Change ssh port in OS X Lion (and Snow Leopard)
time: 2011-07-02
---

{% highlight bash %}
sudo vim /System/Library/LaunchDaemons/ssh.plist

...

 17     <dict>
 18         <key>Listeners</key>
 19         <dict>
 20             <key>SockServiceName</key>
 21             <string>ssh</string> <<< REPLACE 'ssh' WITH PORT
 22             <key>Bonjour</key>
 23             <array>
 24                 <string>ssh</string> <<< REPLACE 'ssh' WITH PORT
 25                 <string>sftp-ssh</string>
 26             </array>
 27         </dict>
 28     </dict>
 
...

sudo launchctl unload -w /System/Library/LaunchDaemons/ssh.plist
sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist
{% endhighlight %}