---
layout: post
title: Nuke, ps grep kill something
---

I have lost count of how many times I have had a rogue process I needed to kill by doing the following:

```bash
ps ax | grep foo
  68105   ??  S      6:58.20 ladidadi foo ladida
kill -9 68105
```

Although this routine is quick to do, it is a bit annoying. I ended up with a little bash function that does this in a single neat command, and thought I'd share.
Just put the following in your .bash\_profile or similar.

```bash
nuke () { ps -ef | grep "$@" | grep -v grep | awk '{print $2}' | xargs kill -9; }
```

Now the same procedure as above is reduced to

```bash
nuke foo
```

Use wisely.
