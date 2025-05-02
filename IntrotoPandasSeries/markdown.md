The syntax to create a series is:

```python
import pandas as pd
pd.Series(data, index, name="A name")
```

`Series`s main components are:

- [ ] **data** : this is the data that we want to represent, and obviously, we could say the "most important" component of the series. In our example, the data is the revenue of the companies.
- [ ] **index** : the index indicates the "labels" of the data we're storing. We'll use the index to "reference" the data later. Indices are not required; pandas will assign a default sequential index if we don't provide one.
- [ ] **name** : a series can contain a "name"; this will make more sense when we start using DataFrames. For now, just think about it as extra "documentation"; more clarity when working with your code. Names are optional.

  **_PRACTICE: Create a series under the variable `my_series` that contains three elements `9`, `11` and `-5`. The index of the series should be `['a', 'b', 'c']` and the name should be `"My First Series"`._**

- [ ] To select several elements (by index/label), we just pass a list of the labels:

```python
s.loc[["Apple", "Intel", "Sony"]]
```

- [ ] To select multiple values by position, we also pass a list with the positions:

```python
s.iloc[[0, 5, -1]]
```

# **Series Attributes and Methods**

1. This returns 5 elements either from the beginning of the series (`.head()`) or from the end of it (`.tail()`)
2.

### Main attributes

Once a series is constructed (somehow), we can access all the attributes separately. Namely:

- The data of the series: using the `.values` attribute
- The index: using `.index`
- The name: using `.name`
- The type assigned: using `.dtype`
- The number of elements: using `.size`
- There's also a `quantile()` method to check for specific quantiles (or percentiles). For example, to get the `75th` percentile, you can use: `s.quantile(.75)`.
- There are also individual methods for each of the values returned by `.describe()`: `.max()`, `.min()`, `.mean()`, `.median()`, etc.

## SORTING SERIES

- To sort the values of the series (that is, the revenue), we use the `.sort_values()` method. To sort the series by its index (in this case, _lexicographically_ by the company's name, we use the `.sort_index()` method. The default sorting method is in "ascending" order. To sort in descending order, you must pass the `ascending=False` parameter (to either method).
- TO SORT IN DESCINDING ORDER:
- s.sort_values(ascending=False).head()
- s.sort_index(ascending=False).head()

## IMMUTABILITY

This is a CRUCIAL concept in Data Science in general. We don't want to change/mutate things, as it's harder to keep track of these changes. When we "sort a series", we don't ACTUALLY sort the series itself. There's a NEW series returned. The underlying series has NOT changed; it has NOT been mutated.

- If by any chance, you DO want to mutate your series, in this case, you want to sort it and alter the underlying series (in `s` in this case), you must pass the `inplace=True` attribute. When doing so, you'll see that this time the method doesn't return anything, but the underlying series (in `s` has changed) to contain the data in the order required.
- s.sort_values(inplace=True)
- s.sort_index(inplace=True)

## MODIFYING SERIES

Modifying series is something we hardly want to do. As mentioned in the previous section, we try to be "immutable". So changing series is usually not recommended.

But still, it's possible to modify series by changing values, adding or removing elements. This works in the same way as with Python dictionaries.

For example, to modify an existing value, we can just "step over it", let's say we want to set IBM's revenue to $0. We can just do:

```python
s['IBM'] = 0
```

To add elements (or change the value of an element, you can just use the index of the new element: `s['Tesla'] = 21450`.

To remove an element, we use the `del` keyword and the index: `del s["Apple"]`.

Again, these are the same ways we use to add/remove elements from dictionaries.

## CONCATENATING SERIES(immutable)

if you want to "concatenate" two series, you can use the `concat()` method `s.concat(dataframe1 or series1, dataframe2 or series2)`.

- another_s = pd.Series([21_450, 4_120], index=['Tesla', 'Snapchat'])
- s_new = pd.concat([s, another_s])

**_The original s will not be modified._**

**_s_new will hold the concatenated series._**
