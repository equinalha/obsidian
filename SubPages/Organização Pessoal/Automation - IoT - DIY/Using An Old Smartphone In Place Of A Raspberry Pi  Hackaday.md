---

---
[https://hackaday.com/2023/04/27/using-an-old-smartphone-in-place-of-a-raspberry-pi/](https://hackaday.com/2023/04/27/using-an-old-smartphone-in-place-of-a-raspberry-pi/)

![[samsung-server-main.jpg]]

The Raspberry Pi was a fairly revolutionary computing device when it came on the scene around a decade ago. Enough processing power to run a full Linux desktop and plenty of GPIO meant almost certain success. In the past year, though, they’ve run into some issues with their chip supplier and it’s been difficult to find new Pis, which has led to some looking for alternatives to these handy devices. [David] was hoping to build a music streaming server [and built it on an old smartphone instead](https://davidhampgonsalves.com/junk-drawer-phone-as-a-music-streaming-server/) of the ubiquitous single-board computer.

Most smartphones are single-board computers though, and at least the Android devices are fully capable of running Linux just like the Pi. The only problem tends to be getting around the carrier or manufacturer restrictions like a locked bootloader or lack of root access. For [David]’s first try getting this to work, he tried to install Navidrome on a Samsung phone but had difficulties with the lack of memory and had to build the software somewhere else and then load it on the phone. It did work, but the stock operating system kept killing the process for consuming too much memory.

Without root access, [David] decided to try LineageOS, a version of Android which, among other benefits, is typically much more configurable than the stock version of Android that is shipped with smartphones. This allowed him to disable or uninstall anything not needed for his music server to free up enough memory. After some issues with transcoding the actual music files he planned on streaming, his music server was successfully up and running on a phone that would have otherwise been relegated to the junk drawer. The specific steps he took to get this working can be found on his GitHub page as well.

[David] also mentioned looking at PostmarketOS for this job which is certainly a viable option for some, but the Linux distribution for phones is only supported on a few devices. Another viable alternative for a project like this if no Raspberry Pis are available might be any of a number of Pine64 devices that might also be sitting around gathering dust, [like the versatile Linux-based Pinephone](https://hackaday.com/2021/09/02/pining-for-a-de-googled-smartphone/).