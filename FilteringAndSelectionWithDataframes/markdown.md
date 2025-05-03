# Filtering and Selection with DataFrames

## BooleanArrays:

A list of boolean values to select specific rows from a pandas DataFrame (`df`). The boolean list corresponds to the rows in the DataFrame, where `True` means the row is selected, and `False` means it is skipped.

### How it works:

- The length of the boolean list == number of rows in the DataFrame.
- Each boolean value corresponds to a row in the DataFrame (in order).
- as shown in the app_01.ipynb file.

## Filtering with .loc()

There are two main methods to "query" (that is, filter) data in DataFrames:

- Using `.loc[]`
- Using `.query()`

1. Check out the app_01.ipynb file to understand.
2. .loc[] is used for selecting or filtering the data, based on what we need.
3. .loc[] is much more powerful and offers more .query(), which is more intuitive or simple.
4. As in our previous modules, remember the syntax of .loc():

   `.loc[INDEX, COLUMNS]`.You can get the number of employees for Apple with: `df.loc['Apple', 'Employees']`

## Combining Expressions with Boolean Operators

Just like in series, we can combine multiple expressions with boolean operators: and (`&`), or (`|`) and not (`~`), for dataframes as well. _(also remember: **DataFrame columns ARE Series as well**)_

1. the companies whose Revenue's is greater than the mean:

```python
df.loc[df['Revenue'] > df['Revenue'].mean()]
```

2. include the companies that are only american, using the `&` operator:

```python
df.loc[(df['Revenue'] > df['Revenue'].mean()) & (df['Country'] == 'USA')]
```

3. filter those companies that are NOT american (note the `~` operator):

```python
df.loc[(df['Revenue'] > df['Revenue'].mean()) & ~(df['Country'] == 'USA')]
```

_check the app_01.ipynb file._

## The .query() method

###### 1. Filtering all the companies from the USA:

```python
df.query("Country == 'USA'")
```

###### 2. Companies which country is different from the USA:

```python
df.query("Country != 'USA'")
```

We enter the name of the column directly, and the value is surrounded with quotes.

#### Boolean Operators

We can include boolean expressions and connectors with `.query()`, use the regular `and`, `or` and `not` operators.

###### 1. Companies NOT from the USA and from the "Consumer Electronics" sector:

```python
df.query("Country != 'USA' and Sector == 'Consumer Electronics'")
```

###### 2. Same as above, but using the `not` operator

```python
df.query("Sector == 'Consumer Electronics' and not (Country == 'USA')")
```

###### 3. Companies that are from China or Taiwan

```python
df.query("Country == 'China' or Country == 'Taiwan'")
```

### Special characters: variables and columns with whitespaces

If you're trying to reference a column that has whitespaces, you must surround the column name with backticks (`):

```python
df.query("`Founding Date` == '04-02-2004'")
```

1. Example

referencing variables from the context, you can prepend the variable name with the `@` character:

```python
mean_revenue = df['Revenue'].mean()
df.query("Revenue > @mean_revenue")
```

2. Example

```python
median_rev_per_employee = df['Revenue per Employee'].median()
df.query("`Revenue per Employee` > @median_rev_per_employee")
```

_suggested: use .loc() preferrably over .query()_
