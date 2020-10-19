# Pandas Cheat Sheet

#### startup
`import pandas as pd`

#### pandas version
`pd.__version__`

`fn = 'mydata.xlsx'`

`df=pd.read_excel(fn)'`

#### read tab-delimited file
`pandas.read_csv(fn, sep='\t', lineterminator='\r')`

#### show all rows
`pandas.set_option('display.max_rows', None) #change None to a number to specify` 

#### read tab-delimited file with specified columns without headers
`df=pd.read_csv(fn, sep='\t', lineterminator='\r',usecols=[2,3,7],names=['Description','ID','Group'])`

#### various ways to import data
`df = pd.read_csv(fn)`

`df = pd.read_json(fn)`

`df = pd.read_sql('select * from mytable', mycn)`

#### if a column is giving problems....
`df=pd.read_excel(fn, dtype={'Job Ticket':object})'`

#### read csv with index
`df=pd.read_csv(fn, index_col=['region','job ticket'])`
`df=df.sort_index()`

#### see a few records from the top and bottom
`df.head(5)`
`df.tail(4)`

#### add new Row

`df.loc[-1] = ["This is a new row","2nd column of new row"]`
#### add a new Column
`df['Address'] = address `

#### add new index
`df.index = df.index + 1`

#### sort index
`df.sort_index()`

#### drop a row
`df = df.drop(df.index[7])`

#### set custom index (use a list)
`index_vals = [1,2,3,4,5]`
`df.index = index_vals`

#### reset the index
`df.reset_index() #old index is still kept in the data`

#### delete old column
`df.drop(columns=["index"])`

#### select 2 columns of dataframe
`df[['name','address']]`

#### show the first 10 rows
`df[['name','address']].head(10)`

#### get row 10 of dataframe
`df.loc[10]`

#### get all rows from index 1 to 4
`df.loc[1:4]`

#### use multiple columns from dataframe
`tempdf=df[["STATE","NAME","CENSUS2010POP"]]`

#### use multiple columns from datataframe with filter
`df3 = df_HBCU.loc[df_HBCU["State/Territory"] == "Alabama", ["School","City"]]`

#### or use names of columns to get all rows starting at index 9
#slice using labels
`df.loc[9:,"Name":"Address"]`

#### iloc only accepts integers.
`df.iloc[2:6]`

#### cannot use string column headers
`df.iloc[2:6, 3:7]`

#### get rows 1,5,7 and all rows
`df.iloc[[1,5,7], :]`

#### conditionals (where clause) # creates a boolean clause 
`df[df["Year"]>1999]`
`df[df["Year"]==1999]`

#### combine statements with 'and'
`df[ (df["Year"]>1999) & (df["Country"]=="USA" ) ]`

#### or statement
`df[ (df["Year"]>1999) | (df["Country"]=="USA" ) ]`

#### not operator is tilde `~`
`df[ ~(df["Country"]=="USA" ) ]`

#### value counts
`df['Country'].value_counts()`

#### groupby - this will return a numpy array
`df.groupby(["staff first name", "staff last name"]).size() `

#### groupby - this will return a dataframe
`df2=df.groupby(["staff first name", "staff last name"]).size().reset_index(name="Count")`

#### groupby - using *agg* with sums and counts
`df.groupby(
     ['Type','Status']
 ).agg(
     Total_Charges = ('Total Charges','sum'),
     Job_Count     = ('Status','count'),
 ).reset_index()
 `
 
#### sum, unique, nunique
#### unique values
df = df["Departments"].unique()


#### sort values
`df.sort_values(['Date'])`

#### pivot tables

`df.pivot(index='processDate',columns='brand',values='cost')`

#### describe function - get some quick stats
df.describe()

#### rename a dataframe column
` df=df.rename(columns = {'col old name':'col new name'})`

#### load a series to a dataframe
`data=df.groupby(["staff first name", "staff last name"]).size()`

`new_df=pd.DataFrame(data=data)`

`new_df=new_df.reset_index()`

`# then change the column names of any column as seen above`







