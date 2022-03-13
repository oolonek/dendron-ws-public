---
id: lXYgpwVweH35j30wEgBhR
title: Pandas
desc: ''
updated: 1646985342234
created: 1609770454495
---

## Subset a df according to string present in columns name

```python
df.loc[:, df.columns.str.startswith('alp')]
```

```python
df.loc[:, df.columns.str.contains('alp')]
```
## Select a df according to column positions

Here from column seven till the end 

```python
df.iloc[:, 7:]
```


## Rename columns

```python
df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'}, inplace=True)
```


## Rename columns or index

```python
df_new = df.rename(columns={'A': 'Col_1'}, index={'ONE': 'Row_1'})
```

Didnt work for me

df_merged_selected.index.rename('Row ID', inplace = True)
 does
## Rename columns by position

```python
df.rename(columns={ df.columns[1]: "your value" }, inplace = True)
```

## Add prefix (or suffix) to colnames

DataFrame.add_prefix(prefix)



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

# Merge two df based on columns


pd.merge(student_df, staff_df, how='left', left_on='Name', right_on='Name')



# replace specific string in values

```python
df['Column2'] = df.Column2.str.replace('b,?' , '')
```

# Replace string by Nan

metadata_lat_lon_df = metadata_lat_lon_df.replace('nd', np.nan)

# Here we observe full NANA rows and full NAN columns in the latest df. We drop them

selected_samples.dropna(how='all', inplace = True) 
selected_samples.dropna(how='all', axis = 1, inplace = True) 




# drop column according to regex

```python
df = df[df.columns.drop(list(df.filter(regex='Test')))]
```

# drop columns according to list


```python
# %%
colsToDrop = [     'BARCODE',            'PLATESET',                'WELL',
            'SUBSTANCE_NAME',        'Full_Species',               'Genus',
                  'Sp_alone',             'Species',             'Famille']

df_merged_selected=df_merged.drop(colsToDrop, axis=1)
df_merged_selected

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
# drop duplicates according to multiple coloumns

DataFrame.drop_duplicates(subset=None, keep='first', inplace=False, ignore_index=False)
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.drop_duplicates.html

df.drop_duplicates(subset=['a', 'b'], keep='first', inplace=True, ignore_index=False)
