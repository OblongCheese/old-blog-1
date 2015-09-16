---
layout: post
title:  "Upgrading Ubuntu Server from 12.04.4 to 14.04.1 directly"
date:   2015-06-22
---

<!-- intro - will be put on main page -->

<p class="intro"><span class="dropcap">U</span>pgrading Ubuntu Server from one major release to another is usually frought with danger, however I decided to go ahead with it anyway...</p>

<!-- write pararaphs as required -->
It all started out fine enough, 

{% highlight ruby %}
sudo apt-get dist-upgrade
{% endhighlight %}

Kicked off the process. I keyed 'y' through the acknowledgements. I watched the mirrors be refreshed and the packages download and install.

The first go-round failed because the installer couldn't delete a file somewhere. So I manually deleted it and started the process over. All good, we made it to the end.

Reboot time.

I rebooted and was disheartened - but not really surprised - to be greeted by the BusyBox bootloader prompt.

{% highlight ruby %}
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
{% endhighlight %}

Sigh. Of course this had to go bad somewhere, right? You can't just jump straight from one LTS release to another without incurring some problems.

Reboot. Watch the kernel messages. See something flash by about unable to read from /boot. OK. 

<!-- insert a picture - probably hosted elsewhere though... -->
<img src="{{ '/assets/img/touring.jpg' | prepend: site.baseurl }}" alt=""> 

<!-- more paragraphs -->
