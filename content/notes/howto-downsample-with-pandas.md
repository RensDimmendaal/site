---
title: "HOW TO: downsample with pandas"
date: 2019-04-22T10:37:35+02:00
tags: howto, pandas
draft: false
---

If you want to create a classifier, but you have an unequal number of observations for each class, then you have to be extra careful with how you estimate your model. If you have a highly imbalanced dataset and optimize for accuracy, then a model might simply predict the majority class in all cases.

A common way of dealling with this issue is downsampling, also known as undersampling.
Downsampling means removing observations from the majority class(es) such that you have an equal number of observations for each class.

To do this in pandas you can use the snippet below.
You should consider using it if you are facing imbalanced classes.

```python
import pandas as pd

def downsample(df, label_col_name):
    # find the number of observations in the smallest group
    nmin = df[label_col_name].value_counts().min()
    return (df
            # split the dataframe per group
            .groupby(label_col_name)
            # sample nmin observations from each group
            .apply(lambda x: x.sample(nmin))
            # recombine the dataframes 
            .reset_index(drop=True)
            )
```

