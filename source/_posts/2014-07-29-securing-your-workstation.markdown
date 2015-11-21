---
layout: post
title: "Securing Your Workstation"
date: 2014-07-29 10:09
comments: true
categories: security
---

With all of the revelations from [Edward Snowden](http://www.theguardian.com/world/edward-snowden) about the unconscionable and patently unlawful (unconstitutional) NSA spying on Americans and the world, here are some tips on how to secure your computer to make it more difficult for this traitorous organization to spy on you.

**1. Use an anonymizing VPN service** 

<img src="../images/anon.jpg" style="float:left; width:350px; margin-right: 10px"/>

You'll want a service that provides a VPN (Virtual Private Network). Many services, like [BTGuard](https://btguard.com/), do not provide a VPN. It only masks your torrent traffic. Whereas a VPN sends all of your network traffic through the anonymized connection.

[TOR](https://www.torproject.org/) (The Onion Router) by itself is not good enough either. TOR is only for **browsing the web** anonymously. It does help but is not foolproof. It doesn't take much for the venal NSA, CIA, FBI, et al. (a.k.a. **Axis of Evil**) to trace back to you, even through TOR. In addition TOR is not a VPN. It only masks your web browsing traffic. 

There are many to choose from. I have my favorite (which I will not divulge) but here is a list of a few anonymizing VPN based proxy services that I know of. I would stay away from free services, which could easily be a front for the previously mentioned Axis of Evil. In reality any of these services could be funnelling data to said Axis of Evil. Trust is all but gone and the 'law' will not help you.

* [AirVPN](https://airvpn.org/)
* [CyberGhost](http://www.cyberghostvpn.com/en_us/proxy)
* [Hide My Ass!](https://www.hidemyass.com/)
* [Hideman VPN](http://www.hideman.net/)
* [IPVanish VPN](http://www.ipvanish.com/)
* [Private Internet Access](https://www.privateinternetaccess.com/)
* [TunnelBear](https://www.tunnelbear.com/) (Free)

We must ask ourselves the important question, do any of these proxy services have backdoors for the Axis of Evil? The answer is, there is no way to know for sure. Life Hacker has an [article](http://lifehacker.com/how-do-i-know-if-my-vpn-is-trustworthy-508866499) about the trust issue.

Even though you are connected to your anonymizing VPN service be careful of logging into any personal accounts. Doing so can provide a means of tracing traffic back to you. It is not possible to forever avoid logging into your accounts (email, et al.). Just be aware that doing so can help reveal you to the Axis of Evil. Think of it this way, if you want to surf the web anonymously then surf the web, but don't login to your email account using the same session. If you want to check email, then login and check email, then disconnect then reconnect to your VPN using a different server and session to browse the web again.

*Note: If you decide to use a VPN service, don't just choose a server in single country and always use it. Switch things up, daily. For example, use Sweden for a day, then switch to Canada the next day. Of course this is assuming the VPN provider you choose has servers in multiple countries. **Hint: Choose a provider with servers in multiple different countries.** Do your own research!*

**2. Frequently modify your MAC address**

A [MAC address](https://en.wikipedia.org/wiki/MAC_address) (or Media Access Control address) is the unique ID for your network interface controller (NIC). It is a hardware serial number but it can be changed using software.

Here is a [script](https://gist.github.com/midwire/79033f2b05f836ecf51b) that I use for changing a MAC address. I use it on OSX but it may work on Linux as well.

It is prudent to change your MAC address at least every bootup. It may be better to change it on a regular schedule as well (i.e., every 24 hours).

*Be aware that this can have the side effect of changing your IP address or confusing certain software or hardware peripherials (i.e., DHCP reservations).*

**3. NEVER use Microsoft Windows!**

<img src="../images/Windows-XP-on-Dell.jpg" style="float:left; width:350px; margin-right: 10px"/>

Microsoft has been [revealed to be working with the Axis of Evil](http://www.theguardian.com/world/2013/jul/11/microsoft-nsa-collaboration-user-data). However, it would be naive to think that Apple or other hardware and software manufacturers are not doing the same thing.

The main problem with Windows is that it is very unstable, insecure, buggy and often full of viruses and trojans. I've been a professional in the computer industry since 1989, and I can tell you (to the dismay of Windows fanboys) that Windows is the abolute worst, most insecure and unstable operating system under widespread use today.

The most secure and trustworthy OS is Linux/GNU. Why? Because it is open source and you and I, and other smarter people, can go read the source code and see what kind of shenanigans may be going on. Does that provide any guarantees? Absolutely not. Case in point, the [Heartbleed bug](https://en.wikipedia.org/wiki/Heartbleed) in SSH.

Personally, I use OSX and have found Apple hardware to be far better than any other. In the past I've built my own high-end machines and owned Dells, Gateways, etc. It took a long time for me to jump in and purchase a more expensive Apple computer. Once I did the fog was lifted from my eyes. I've still got the first MacBook I purchased after the turn of the century. It still works wonderfully, albeit slowly. Macs just work, and when you drop one on the sidewalk Apple customer service has proven to be the best in the world.

**4. Use Firefox**

<img style="float:right" src="../images/firefox_logo.jpg" />

As a software engineer, most of my colleagues choose to use Google Chrome as their browser of choice. My own personal view is that since [Google itself frequently hands over data to the Axis of Evil](http://america.aljazeera.com/articles/2014/5/6/nsa-chief-google.html), why on God's green earth would I use a browser that was developed at the same company?

In my opinion, [Firefox can be secured](http://midwire.github.io/blog/2013/07/22/minimizing-nsa-prism/) better than Chrome and Mozilla (the company behind Firefox) is not beholden to Google.

**5. Don't Use Google**

<img src="../images/d-google-evil.jpg" style="float:left; width:350px; margin-right: 10px"/>

As stated in a [previous article](http://midwire.github.io/blog/2013/07/22/minimizing-nsa-prism/), Google is evil, period. Don't use it for your search engine, email, their DNS servers (8.8.8.8 and 8.8.4.4). Avoid Google like the plague. See the linked article for alternatives.

There are also [alternative DNS providers](http://www.wikileaks.org/wiki/Alternative_DNS).

*You can tell I hate Google. And, as is with most websites that are critical of them, you will never find high-ranking links back to this site in their index.*

<p></p>
**6. Watch Your Traffic**

<img style="float:right" src="../images/Little_Snitch_Network_Monitor.png" />

As with anything important, pay attention! Watch your IP traffic over the network. On Linux or OSX you can use [iptraf](http://iptraf.seul.org/) or [iftop](http://www.ex-parrot.com/pdw/iftop/) to watch where your traffic is coming and going. You may spot some interesting hostnames like 'gv-in-f103.1e100.net', which is Google. Using 'iftop' I found an app that was connecting to Google from my machine. Those insidious bastards!

Note: Little Snitch also provides a traffic monitor.

**7. Use a Firewall**

Whether you use the built-in firewall and tools that come with your operating system or purchase a full-blown professional firewall appliance, don't neglect the firewall.

Personally, I use the built-in OSX firewall and Little Snitch on my own machines. In addition my LAN is sealed off by a ZyXEL, ZyWALL USG 50.

I highly recommend [Little Snitch](http://www.obdev.at/products/littlesnitch/index.html) for OSX users. Iptables works wonderfully for Linux/GNU users.

**8. Use Encryption**

<img src="../images/encryption.jpg" style="float:left; width:350px; margin-right: 10px"/>

Just like a padlock on a locker, if someone wants to break-in they will cut the lock. We just want to add as many locks to our data as possible. Our locks are encryption. 

* Encrypt your email using GPG. Encourage your friends and family to do the same.
* Use HTTPS (SSL) instead of HTTP wherever possible. Even though [SSL is clearly hackable](http://www.darkreading.com/attacks-and-breaches/https-hackable-in-30-seconds-dhs-alert/d/d-id/1111040?) or [circumventable](http://stackoverflow.com/questions/14907581/ssl-and-man-in-the-middle-misunderstanding), it is another 'lock' that takes time to successfully break.
* Use SSH for point-to-point remote connections and tunnelling.

## Summary 

Understand that the corporate government of America owns, or sits on, all the major switches on the Internet. They have access to all traffic and funnel it into their [Utah Data Center](https://en.wikipedia.org/wiki/Utah_Data_Center). If they want to track you, it cannot be stopped. All you can do is make it more difficult for them. But if you are on one of their many lists, the only way to have computer privacy is to detach it from the internet, and even that guarantees nothing.

Welcome to the world we live in.

-- Midwire
