## vectorizing with Pandas and NumPy 
- https://gitlab.com/cheevahagadog/talks-demos-n-such/tree/master/PyGotham2019
- [local cloned notebook](https://github.com/er1czz/writeup/blob/main/tech/PyGotham-updated.ipynb)
- a quick example
    - if payer_name contains any keywords, such as "BCBS","BC", "BS", "BLUE","SHIELD", "CROSS"
    - if their payer_id have 3 characters
    - then add "SB" prefix to the payer_id
```
import pandas as pd
import numpy as np
# create test data
payer_data = {"BCBS  NH":"7422",
                "BCBS  NH ":"212",
                "BLUE SHIELD NH":"71",
                "BLUE SHIELD NH ":"710",
                "BLUE CARE KY":"32002",
                "BLUE CARE KY ":"803",
                "BC BS OF AZ":"171",
                "BLUE SHIELD NH":"389",
                "BC NY":"180",
                "BS NJ ":"153"}
                
df = pd.DataFrame(payer_data.items(), columns  = ['payer_name', 'payer_id'])

# create list of keywords
keywords = ["BCBS","BC", "BS", "BLUE","SHIELD", "CROSS"]

# create condition
conditions = (df['payer_id'].str.len()==3) & (df['payer_name'].apply(lambda x: any(k in x for k in keywords)))

# apply condition
df['payer_id2'] = np.where(conditions, 'SB' + df['payer_id'], df['payer_id'])

        payer_name payer_id payer_id2
0         BCBS  NH     7422      7422
1        BCBS  NH       212     SB212
2   BLUE SHIELD NH      389     SB389
3  BLUE SHIELD NH       710     SB710
4     BLUE CARE KY    32002     32002
5    BLUE CARE KY       803     SB803
6      BC BS OF AZ      171     SB171
7            BC NY      180     SB180
8           BS NJ       153     SB153

```

### a common error in Numpy vectorization
- TypeError: invalid entry 0 in condlist: should be boolean ndarray
```
df = pd.DataFrame({"col1": list("ABBC"), "col2": list("ZZXY")}).astype("string")
conditions = [
    df["col2"]=="Z",
    df["col2"]=="X",
    df["col1"]=="B"
]
choices = ['yellow', 'blue', 'purple']
df['color'] = np.select(conditions, choices, default='black')
```
- Cause: np.select() expects an ndarray of type bool
- Fix: to cast it to the correct type with .astype(bool)

```
df = pd.DataFrame({"col1": list("ABBC"), "col2": list("ZZXY")}).astype("string")
conditions = [
    (df["col2"]=="Z").astype(bool),
    (df["col2"]=="X").astype(bool),
    (df["col1"]=="B").astype(bool)
]
choices = ['yellow', 'blue', 'purple']
df['color'] = np.select(conditions, choices, default='black')
```

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
