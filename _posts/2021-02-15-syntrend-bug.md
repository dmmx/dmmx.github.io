---
layout: post
title: "Syntrend Bug"
---

Browsing through [Atarimania](http://www.atarimania.com/) I stubbled across [Syntrend](http://www.atarimania.com/list-atari-magazines.html), an application from Synapse software that, among other things, performs linear regression.
Intrigued, I download the disk image and the manual and started going through the tutorial. Everything seemed to be going well except that the
Analysis of Variance page seemed messed up:

![Garbled Analysis of Variance](/assets/images/aov_messed_up.png)

Syntrend not only does linear regression on a single variable, it does multiple regression as well. The tutorial for multiple regression starts on page 46, and on page 48 it shows the coefficient values for the two variables `AUTOEXP` and `TELEXP`. However when I actually tried this, the second variable
`TELEXP` was missing.

![Missing TELEXP Variable](/assets/images/missing_telexp.png)

To troubleshoot the error I tried doing a single variable regresson on `TELEXP`. This resulted in an `ERROR 9`:

![ERROR 9](/assets/images/error_9.png)

For reason I do not quite understand this error bothered my for a long time. I know that in Atari BASIC `ERROR 9` was an "Array or String __DIM__ Error, but I could not think of how that error applied to this situation. I tried everything. I rearranged the data, reformatted the disk, started the tutorial over again. Finally I noticed that `TELEXP` was one letter shorter than `AUTOEXP` so I increased the number of letters from six to seven by renaming the variable to `PHONEXP`.

![PHONEXP](/assets/images/phonexp.png)

Amazingly this fixed the error and the multiple regression tutorial worked as advertised.

![Fixed !!](/assets/images/fixed.png)

