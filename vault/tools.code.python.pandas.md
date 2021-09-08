---
id: lXYgpwVweH35j30wEgBhR
title: Pandas
desc: ''
updated: 1613047620747
created: 1609770454495
---

## Subset a df according to string present in columns name

```python
df.loc[:, df.columns.str.startswith('alp')]
```

```python
df.loc[:, df.columns.str.contains('alp')]
```

## Rename columns

```python
df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'}, inplace=True)
```
## Rename columns by position

```python
df.rename(columns={ df.columns[1]: "your value" }, inplace = True)
```

## Check df datatype

```python
df.dtypes
```

## Convert to a specific type

```python
df.year.astype(int)
```

# From continuous to categorical 

```python
pd.cut(df.Age,bins=[0,2,17,65,99],labels=['Toddler/Baby','Child','Adult','Elderly'])
```


# Merge two df based on index

```python
pd.merge(df1, df2, left_index=True, right_index=True)
```

# replace specific string in values

```python
df['Column2'] = df.Column2.str.replace('b,?' , '')
```

# drop column according to regex

```python
df = df[df.columns.drop(list(df.filter(regex='Test')))]
```

# If Na replace with value of the same row but another column

https://stackoverflow.com/a/29177664

```python
df.Temp_Rating.fillna(df.Farheit, inplace=True)
del df['Farheit']
df.columns = 'File heat Observations'.split()

```

# Extract digits from a string 

https://stackoverflow.com/a/37683738


```python
df.A.str.extract('(\d+)')
```

# Create multiples columns values conditionally using np.where
https://stackoverflow.com/a/19913845

```python
df = pd.DataFrame({'Type':list('ABBC'), 'Set':list('ZZXY')})
conditions = [
    (df['Set'] == 'Z') & (df['Type'] == 'A'),
    (df['Set'] == 'Z') & (df['Type'] == 'B'),
    (df['Type'] == 'B')]
choices = ['yellow', 'blue', 'purple']
df['color'] = np.select(conditions, choices, default='black')
print(df)

```


pklaceholder


