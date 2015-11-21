---
layout: post
title: "EVGA UV + 19: Mac Third Monitor Testing"
date: 2012-01-07 11:45
comments: true
categories: [mac,osx,lion]
---

*Disclaimer: I am not paid to review products.  This post is here in hopes that it will benefit someone wanting more than 2 monitors for their Macbook laptop.  If you do happen to click on one of the Amazon links below and purchase one of these products, Amazon will add a few cents to a gift card for me to use the next time I want to buy a Kindle book.*

As a software engineer I value my Mac hardware a great deal.  My ideal setup would be a [Mac Pro](http://www.apple.com/macpro/) tower at the office, with 3-4 monitors and more RAM than I would ever use.  However, in this business we need to be mobile so we can work at the office, from home or while we are at the beach in Belize.  Onsite is almost always out of the question, but that is another rant.

So, we are stuck with our Macbook Pros supporting only 8GB of RAM and a single external display.  Us Mac users really love the ability to attached a huge second monitor to our Macbook Pros.  It is invaluable for software development, especially when pairing remotely, but a third monitor would be even better.  After looking at several different options I came up with two likely solutions.

1. [EVGA UV + 19](http://www.evga.com/products/moreInfo.asp?pn=100-U2-UV19-TR&family=USB&sw=10): $58.49 from [Amazon](http://amzn.to/ymMVwj)
1. [Matrox TripleHead2Go](http://www.matrox.com/graphics/en/products/gxm/th2go/): $306.99 from [Amazon](http://amzn.to/zfkB8q)

With Amazon's excellent return policy, I decided to start with the less-expensive EVGA solution.  If it doesn't work I will return it and spring for the Matrox hardware.

I got the UV Plus from Amazon within 3 days.  Opened up the package and found the following:

* The small 2.5-inch square device, 7/8ths of an inch thick
* A retractable USB cable
* A VGA-DVI adapter

![EVGA UV Plus](/images/EVGA-UV-Plus.jpg)

I planned to try out the device at the office where my large third monitor lives.  Being impatient as I am, I decided to install the driver and hook it up to my second large monitor which lives at home, and is usually plugged into the mini-dvi on my Macbook Pro.  Installing the driver requires a reboot, but after I found that the device does indeed work.  The video had a slight, noticeable lag when moving the mouse or dragging a window.  But the Display manager worked and allowed my Macbook to arrange what it considered a new monitor, and I could drag things to it and away from it.

Being happy that it worked, I unplugged the device and plugged my second monitor back into the mini-dvi interface.  My Macbook then began acting increasingly strange.  Apps started being unresponsive and everything start to crawl along at intolerably slow speeds.  Finally, I uninstalled the driver using the uninstall icon that came with it and everything went back to performing normally.

Before I send it back I plan to try it again at the office where I can leave the third monitor hooked up.  I have a feeling that the EVGA device will end up being returned in favor of the Matrox solution.

Stay tuned for updates...

---

Update: 01/10/2012: After setting up my 2 external monitors at the office, re-installing the DisplayLink (EVGA Plus) driver, and plugging everything in, I am extremely pleased to announce that everything works!  No race-conditions occur, even when unplugging the EVGA monitor.  I have a feeling that plugging in a monitor to the EVGA device that was previously setup as an OSX native second monitor causes race conditions.

![3 Monitors](/images/3_monitors.jpg)

Anyway, now I have three monitors and my development setup couldn't be more perfect.  Another monitor would cause me to strain my neck :)

Conclusion: For less than $60.00 USD. the [EVGA UV Plus 19](http://amzn.to/ymMVwj) works!  This makes me extremely happy!

---

Update: 01/17/2012: Another few days went by and I have started to see problems.  Processes seem to be running slow, video on all three monitors seems to jump and be slow as well.  The actual CPU usage is very low but nevertheless performance has started to suffer.  Unfortunately I cannot tolerate these kinds of issues during a typical workday.  I have uninstalled the driver.  Will give it one more shot before I send it all back.  At this point I am disappointed.  I may make one more updated entry if anything changes (i.e. if performance doesn't drop off during my next test).  Otherwise I have changed my conclusion.

Updated Conclusion: The driver still seems a bit buggy.  Performance suffers intermittently.  Work becomes intolerable.  If you don't want to deal with these kinds of issues, I sadly recommend not using this product.  Hopefully the DisplayLink people will fix the driver issue soon.

Update: 06/27/2013: After a year and a half of using the EVGA UV Plus 19 I can say that the initial weirdness has gone away.  Every now and then it will do strange things like lag severely but overall it works pretty well.  For the money spent I cannot complain.

-- Midwire
