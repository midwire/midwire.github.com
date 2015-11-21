---
layout: post
title: "A Portable Bash Environment"
date: 2011-08-15 12:33
comments: true
categories: [bash,linux,osx,solaris,bsd]
---
Working with computers over the years I've built up a set of shell environment preferences, aliases, functions, etc.  [Bash](http://tldp.org/LDP/abs/html/) is my shell of choice and incredibly powerful if used correctly.

My [Macbook](http://www.apple.com/macbookpro/ "Macbooks are awesome!") Bash environment sports a plethora of command [aliases](http://tldp.org/LDP/abs/html/aliases.html) and [functions](http://tldp.org/LDP/abs/html/functions.html) that make work relatively easy.  My shell preferences are all neatly stored and sourced on opening the Terminal application.  However, I am often required to login to new servers to do work.

A new, default Bash environment makes me cringe.  Missing my tools and aliases makes things very frustrating.  For example when I want to change directories up three times, in my home environment I can just type `3..` instead of `cd ../../..`.  When I try to type `3..` and the shell barfs back `-bash: 3..: command not found`, it gives me that "oh crap" feeling.

To help solve this situation I published my [environment on GitHub](https://github.com/midwire/.env "Midwire's Bash environment on GitHub").  Now I can just login to the new box, `clone git://github.com/midwire/.env.git`, then add the following to my `.bashrc` file:

{% codeblock Append this to your .bashrc file %}
[[ -r $HOME/.env/source.sh ]] && . $HOME/.env/source.sh
{% endcodeblock %}

This recursively sources each `*.sh` file beginning with your `~/.env` directory.  What I like about this as opposed to the all-in-one `.bashrc` file is that it keeps everything compartmentalized for easy maintenance, and it's portable from a location standpoint.

The next step is to make it portable from a platform standpoint.  For instance, I want to have the environment get sourced according to the type of platform it is on.  In other words, if I am on a [Solaris](http://en.wikipedia.org/wiki/Solaris_%28operating_system%29) box the aliases and functions may need to be different in comparison to a Mac OSX box.

Feel free to clone the [repository](https://github.com/midwire/.env), update and send me a pull request.

Cheers,

-- Midwire
