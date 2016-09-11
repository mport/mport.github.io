--- 
layout: post 
title:  "Disable Dell XPS 13 Touchpad on Ubuntu 16.04"
date:   2016-09-10 21:00:00
categories: ubuntu dell-xps-13 
---

I've recently got my shiny, new Dell XPS 13 (9350). After installing Ubuntu 16.04,
everything worked without a hitch. Excellent. One thing that did bother me
however was inadvertently hitting the touchpad while typing.

Here is a simple solution to enable/disable the
touchpad on-demand via keyboard shortcuts:

1. Figure out the id of your touchpad:
  <br /> 
  `xinput list`

2. On my laptop, the id is 12. Touchpad can be turned on/off as follows:
  <br /> 
  `xinput enable 12`
  `xinput disable 12`

3. To configure the keyboard shortcut, use:
  <br /> 
  `System Settings => Keyboard => Shortcuts`


That's it. :-)



