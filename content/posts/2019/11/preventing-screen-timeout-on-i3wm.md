Title: preventing screen times out in i3 wm 
Date: 2019-11-30 11:00
Category: system administration 
Tags: linux, xorg 
Author: Vitor Carvalho 
Slug: preventing-screen-times-out-in-i3-wm 
Summary: I'm currently using Linux with i3 Window manager with an external monitor with a thinkpad dock station.  Sometimes I get afk for too long and the screen goes black and I'm unable to turn it on again, and I don't know why.


I'm currently using Linux with i3 Window Manager and an external monitor
plugged into a thinkpad dock station.  Sometimes I get afk for too long and the
screen goes black and I'm unable to turn it on again, only if I deattach the
notebook and attach it back. I don't know why this happens.

So I decided to look for a way that the monitor doesn't turns black in such
situations. The first thing I found out is that Xorg has a small screen saver
functionality builtin. It allows the system to goes into standby or suspend
mode.

Searching the web I found this [link](https://askubuntu.com/questions/763994/screen-times-out-in-i3-wm) 
from Ask Ubuntu, the answer teaches how you can disable this Xorg funcionallity
completely.

All you have to do it's to use the xset tool.

```
xset -dpms
xset s off
```

The `-dpms` option disable DPMS (Energy Star) features, on the other hand, the
option `+dpms` enable it (from xset man page).
The `s` option allows you to set screen saver parameters, in this case, we are
turn the screen saver off.

Now my external monitor never get black screen. I always execute this 2 lines
of code when I put the notebook in my dock station.
