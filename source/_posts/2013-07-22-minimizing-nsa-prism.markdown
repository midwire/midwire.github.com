---
layout: post
title: "Minimizing NSA PRISM"
date: 2013-07-22 11:39
comments: true
categories: [mac,osx]
---

With the recent revelation about the [illegal NSA spying on American citizens](https://www.eff.org/nsa-spying/timeline), it is advisable to do what we can in order to curb or limit the NSA's ability.

Below are some of the ways you can do this.

## Browser

### Use Firefox

Why would anyone want to use Google's Chrome browser when they (Google) are the largest provider of PRISM data in the world? Does anyone actually trust Google with their data? The question is obviously rhetorical since we know that millions of users use Google services and applications.

Firefox allows extensions. I don't want to get into any religious argument over why Chrome, Opera, Safari or any other wannabe browser is better. The fact is that Firefox, with the right extensions, is the safest, most secure browser available today. Just use it!

There are some very good extensions that I would simply not want to live without:

* [NoScript](http://noscript.net). NoScript disables Javascript by default. When you need to use Javascript you simply allow it temporarily. There is no good reason to allow Javascript to run on every web page you visit. It can be malicious and is the number one way for companies and governments to track you on the web, so why trust it?
* [Ghostery](http://ghostery.com). Ghostery notifies you of, and blocks by default, web tracking through cookies, invisible pixel images, etc.
* [Disconnect](http://disconnect.me). Another plugin to help prevent tracking on the web. This will catch most anything that Ghostery doesn't.
* [MaskMe](http://www.abine.com). MaskMe's free email masking is perfect for eliminating spam. It provides masked emails on the fly and forwards emails until you tell it to stop. Let's say you go to a job hunting website like monster.com and sign up using a MaskMe email address like 'abcdefg@opayq.com'. When Monster sends you an email it gets forwarded to your real email address. But all of a sudden one day you start getting emails from jobhat.com, and other such websites that you never signed up for. Simply disable or block that particular masked email and the spam goes away, forever. Never give out your real email address again. Ever!

### Search Engine

Then there is the search engine. I remember back in the 90's when Google was just trying to hold their own next to Yahoo. I was a big Google evengelist because I didn't, and still don't, like mega-corporations and the data they collect. Google has since become far more nefarious than Yahoo ever was. They actively participate in the illegal NSA PRISM program, and every time you search using Google your information is captured and stored for future use against you in a criminal, or possibly military, court. In addition most websites now use Google analytics, Google fonts or Javascript stored on Google.  That means every time you visit a website that uses one of these services, Google tracks and saves a record that you, "insert name here", visited that particular website, the time of day, what you clicked on or downloaded and possibly any data you entered while there.

It is purely speculation, but what happened to all of the legal trouble Google was in back in 2012? There were antitrust issues, alleged copyright infringments and other alleged predatory practices. All of that seemed to silently just go away before this new PRISM revelation.  Coincidence? I think not. Google has likely made a deal with the US government to provide private information in return for prosecution exemptions.

Let's face it... Google is evil! Period.

Use [Startpage](https://startpage.com) or [Ixquick](https://ixquick.com) for a more secure search experience. They are from the same company and located in the Netherlands.

Startpage provides anonymous Google results, and Ixquick provides a separate index, but both aparently privately as they say they do not track your IP address or use cookies for anything but storing preferences.

### Operating System

It is clear that Microsoft and Apple are both participating in the PRISM program. The safest OS is Linux-GNU. Why? Because you can download, examine, modify and compile the kernel and all of the GNU tools and utils. That said, OSX (a FreeBSD derivative) can be made relatively safe as well.

I will not personally use Windows, ever. Nor will I allow anyone in my immediate family to use any of the horrible and unstable Microsoft operating systems.

#### OSX

If you use OSX, as I do, it is simply a must to purchase and learn to use [Little Snitch](http://www.obdev.at/littlesnitch).

I also own an Apple Airport router. Recently I fired up my AirPort Utility application and Little Snitched warned me that it (AirPort Utility) was trying to send information to "dni.gov"! I am not kidding. The Director of National Intelligence website! This is a good site to block, so I told Little Snitch to never let any of my applications contact dni.gov. Of course they will likely modify their code to use some arbitrary IP address, to which I will promptly block as well. Using Little Snitch, always block unless you are sure of the traffic you are allowing. If you have a question about a particular IP address or application use Startpage to search for answers.

Do NOT use iCloud if you are using an Apple product. Just turn it (iCloud) off and store your data locally. Backup to USB drives or external drives but never use their cloud.

## Cloud Services

Avoid cloud services like DropBox and obviously GoogleDrive when storing any sensitive information. It is also a good bet that Amazon cloud services are part of PRISM. Avoid if possible.

## Email

It is difficult to find a proven secure email hosting service. Even [Hushmail has its issues](http://www.wired.com/threatlevel/2007/11/encrypted-e-mai/). A good alternative is to encrypt your own email and when sending unencrypted email to anyone, just assume that the NSA and every other government agency will get their eyes on it.

### Encryption

Mac users have a wonderful option in [GPGMail](https://gpgtools.org/gpgmail/). The main drawback is that most users don't understand or use email encryption. You cannot send an encrypted email to anyone who does not have a public key.

Spread the word and convince everyone you know to use GPG encryption for their email.

## Conclusion

Lastly, avoid non-free scanning programs like: [PrivacyScan](http://privacyscan.securemac.com/) that supposedly do everything for you at the click of a button, for a price. They can do a few good things but they will not change your bad habits or force you to use Firefox and GPG encryption. You can do more to protect yourself by following the ideas and tips in this article or doing your own research for free.

