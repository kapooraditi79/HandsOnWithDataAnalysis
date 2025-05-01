# VECTORIZED OPERATIONS

With Series, it's going to be pretty much the same, it might look even simpler.

First, we initialize the Series we've been using, this time we name it `revenue_in_millions`. It captures the revenue of the companies in Millions of dollars.

We then create **A NEW** Series named `revenue_in_billions` just by dividing the whole Series by `1000`:

```python
>>> revenue_in_billions = revenue_in_millions / 1000

Apple                274.515
Samsung              200.734
Alphabet             182.527
Foxconn              181.945
Microsoft            143.015
Huawei               129.184
Dell Technologies     92.224
Meta                  85.965
Sony                  84.893
Hitachi               82.345
Intel                 77.867
IBM                   73.620
Tencent               69.864
Panasonic             63.191
```

That's a vectorized operation. We say it's "vectorized" because it doesn't act on just 1 value, but in the whole _vector_ of values contained in the Series.
