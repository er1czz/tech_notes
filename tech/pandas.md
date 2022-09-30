## show rows contains keyword
``
df[df['procedurecode'].str.contains("D27", na = False)]
``
- target column 'procedurecode'
- keyword 'D27'


## common group by
``
df.groupby(['cpid'])['counts'].sum().reset_index().sort_values('counts', ascending = False)
``
- group by column 'cpid'
- summation on colum 'counts' 
- reset_index to clean the table
- order by counts DESC

``
SELECT cpid, SUM(counts) counts
FROM df
GROUP BY cpid
ORDER BY counts DESC;
``

## show specific rows and columns
```
df.iloc[0:5] # first five rows of dataframe
df.iloc[:, 0:2] # first two columns of data frame with all rows
df.iloc[[0,3,6,24], [0,5,6]] # 1st, 4th, 7th, 25th row + 1st 6th 7th columns.
df.iloc[0:5, 5:8] # first 5 rows and 5th, 6th, 7th columns of data frame 
```
## show specific rows with column names as a dataframe
```df.iloc[[i]]```
