---
layout: post
title: "Mask Your IP Address For Fun And Profit"
date: 2020-06-04 15:59:55 -0600
comments: true
categories:
---
Why would anyone want to mask or change their IP address? There are many possible reasons, but here are a few:

1. You work remotely and your company requires a static IP address for whitelisting purposes
1. Your ISP (school, company) locks down certain things so you cannot access them
1. You don't want reveal your physical location through your web traffic

It is a simple matter to build an SSH tunnel which will mask your true IP address, and subsequently your physical location.

First you need an SSH login account at a remote location.  [Linode](https://www.linode.com/?r=ead21ade75a93f69f3407f7dfaa98694c878efc8) offers stable Linux nodes for as little as $5/month.  (NOTE: This link gives me a referral credit)  You can also use Amazon Web Services or any other hosting provider or shell account provider.  At a minimum you need SSH access.

Once you get your account setup, you can use SSH to build a tunnel which will look like this in concept.

![SSH Tunnel](/images/ssh-tunnel.png)

Let's see what your current IP address is by heading to [IPChicken.com](https://ipchicken.com).

Let's say your real IP address is `abc.def.ghi`.  Once you build the tunnel, all sites that you access will think your IP address is `qwe.rty.uio` instead of `abc.def.ghi`. And any traffic between Your Computer and the SSH Node will be encrypted.

To build the tunnel use SSH like this in your Terminal or iTerm app.

{% highlight bash %}
ssh -D 8080 -CqTnN username@tunnelhost.com
{% endhighlight %}

Here's what those command-line switches mean:

{% highlight bash %}
-D - [bind_address:]port
-C - Request data compression
-q - Quiet mode
-T - Disable psuedo-terminal allocation
-N - Do not execute any remote commands
-n - Redirect stdin from /dev/null (actually, prevents reading from stdin)
{% endhighlight %}

It may prompt for your password. Now you can use port 8080 for any traffic you want to be masked.

Configure your browser to use an HTTP SOCKS proxy. For Firefox it looks like this:

![Firefox SOCKS Proxy](/images/firefox-socks-proxy.png)

Once you get that setup, head over to [IPChicken.com](https://ipchicken.com) again to see your brand new IP address!

Have fun!
