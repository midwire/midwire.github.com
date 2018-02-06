---
layout: post
title: "Prevent MacOS Applications From Adding Launch Agents"
date: 2017-04-18 13:16:16 -0500
comments: true
categories: [mac,osx]
---
Many OSX users don't realize that applications can install their own launch agents[^1] without you ever knowing it. I found this out because I use some software called Drive Genius to monitor my hard drives and their health, which watches the launch agent folders for new files or changes to existing files. When it detects any changes it pops up a notification like this:

<img src="../images/launch_agent_warning.png"/>

You can find a similar, free, offering here called CIRCL automatic launch object detection: http://www.circl.lu/pub/tr-08/

When I catch an application doing that I use AppleScript to write a launcher which will launch it and then delete any launch agent that it drops.

```applescript
# Launch Amazon Music and remove it's attempt to force itself into your login items

tell application "Amazon Music" to activate

tell application "System Events"
  set startupItems to (name of every login item)
  repeat with i from 1 to count of startupItems
    if startupItems's item i is equal to "Amazon Music" then
      delete login item "Amazon Music"
    end if
  end repeat
end tell

delay 3

tell application "Finder"
  delete (every item of folder "LaunchAgents" of folder "Library" of folder "cblackburn" of folder "Users" of startup disk whose name begins with "com.amazon.music")
end tell

do shell script "/bin/launchctl remove -w com.amazon.com"
```

Just modify it to your needs and it should help keep unwanted launch agents at bay.

[^1]: A launch agent is similar to a cron job, but OSX specific.
