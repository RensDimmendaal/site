---
title: "HOW TO: plot inline in ipython with iterm2"
date: 2019-04-22T10:44:35+02:00
tags: howto
draft: false
---


Inline plotting in the terminal is useful if you want to do some quick analysis without launching a full jupyter notebook.
I'm going to show you how to get inline plots in ipython console with iterm2.

First, install this python package called [imgcat](https://github.com/wookayin/python-imgcat):

```bash
$ pip install imgcat
```

Second, fire up an ipython console and run:

```python
import matplotlib
matplotlib.use("module://imgcat")
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax = plt.plot([1,2])
fig.show()
```

You should see the following:

<img src="/img/ipython-plot.png" alt="example plot in ipython"
	title="Example Plot in Ipython" width="50%" />

There, now I've shown you how to get inline plots in the ipython console in iterm2.
You should go out and do your data sciency stuff in the terminal.

**Bonus,** be friendly to your future self and add the first steps to your ipython default profile:

```bash
$ cd ~/.ipython/profile_default/startup
$ touch my_custom_startup.ipy #note the .ipy extension
```

My startup file looks like this:

```python
%load_ext autoreload
%autoreload 2

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

import matplotlib
matplotlib.use("module://imgcat")
```
