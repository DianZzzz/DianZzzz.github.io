---
layout: blog
topic: Python
title: Python Cheatsheet
tags: python
comments: true
date: 2022-06-11
---

# Python Cheatsheet

## Preparation

```Python
%pylab inline
import warnings
warnings.filterwarnings('ignore')

from google.colab import drive
drive.mount('/content/drive')

users = pd.read_csv('users.dat',
                    nrows = 100000,
                    sep='::',      # use this field separator
                    index_col=0, # set first column as index
                    header=None,   # do not use the first line as a header
                    names=['user_id', 'gender', 'age', 'occupation', 'zip'],
                    engine='python',
                    parse_dates = ['Created Date']) # change datatype to date

df.info()   
df.describe()      

# number of observations in the dataset
df.shape
df.shape[0] # number of rows
df.shape[1] # number of columns

#type()
df.column_name.dtype
df.dtype['column_name']

# check for each category in categorical variables
for col in list(df.columns):
    if type(df[col].unique()[0]) is str:
        print(col,df[col].unique())

#get all unique values
list(nyc['Complaint Type'].unique())
```

## Preprocessing

```Python
from datetime import datetime
df.duplicated() # check for duplicates
df.isnull().sum() # check for null
df.isnull().sum().sum() # check for total # of nulls across all columns and rows
df[df['GMV'].isnull()] # isolate null rows

## Fiill NaN
df.fillna(0)

## drop NaN
df.dropna(axis=1, how='all').dropna(axis=0, how='all') # any or all

# set values to NaN
df.replace(0, np.nan)
df['column'].replace({0:np.nan, 1:2})

# drop duplicates
df[['Id', 'AnswerCount']].drop_duplicates()
df.drop_duplicates(subset='Incident Zip')

# check if all values are unique
df['column'].is_unique

# convert string to numerical
pd.to_numeric(crsp['SICCD'], 'coerce')

# convert to string
raw['text'].astype(str)

#convert date column to a datetime object
df['Date'] = pd.to_datetime(df['Date'])
crime['Year'] = pd.to_datetime(crime['Year'],format='%Y')

#rename columns
df.rename(columns={'category_gold':'# of ratings'})
iris.columns = ['sepal_length','sepal_width', 'petal_length', 'petal_width', 'class']
```


## Lists

``` Python
#last element of a list
x[-1]
#last three element of a list
x[-3:]
#every second item of the full list
x[::2]
#slicing
x[2:5]
[3, 4, 5]
# modify a  list
t[2:4] = ['C', 'D']

a.pop(index)# delete/remove element from a list
a.upper()
a.lower()
a.index(value) #return the index of the value

#remove all duplicates from a list
unique = list(set(test_list))

# enumerate() gives the list index and list item together
for index, item in enumerate(a):
    print('Item number', index, 'is', item)

#flatten a list
import itertools
merged = list(itertools.chain(*list1))


list(dictionary.keys()) # returns a list of keys

list(dictionary.values()) # returns a list of values

list(dictionary.items()) # Returns all (key, value) pairs as a list of tuples.

# change/update dictionary
dictionary[key] = value

#copy list
a = [1, 2, 3, 4]
b = a       # Create a "copy"
b[2] = 9 # Modifying either list also modifies the other list

#create independent copy
import copy
c=copy.deepcopy(a)
```

## Regex
``` Python
import re
re.findall('pattern', string) #return a list of matches
re.match #match must take place at the start of the string
re.search #returns true or false; does not limit to the poition of the match
re.sub()
#[abcd] matches any one of 'a', 'b', 'c', 'd'
#[^abcd] mathces anything except the charaters in the bracket
#[0-9] or \d matches any digit
#[a-zA-Z0-9] matches any alphanumerical characters
# \w = [a-zA-Z0-9_]
#\s for a space or a tab
#. match any character
#\. match the full stop sign
#\w* matches zero or more
#\w+ matches one or more
#\w? matches zero or one times; https? mathces both 'http' and 'https'
#\b...\b used for matching a word
# | or
# ...(pattern)... return only the part inside the bracket
# (?=(pattern)) searches for overlapping patterns; so search for 'aa' in 'aaa' would return two 'aa'
# (?<= )patterns you want to find(?=)
# (?<!^) pattern not at the begining
# {2,} at least two occurences
# \d{3}(?:\d{3})? 3 or 6 digits exactly
```

## Dataframe
``` Python
#create an empty dataframe
comments = pd.DataFrame(columns = ['Date','user_id','comments'])

# create a dataframe from a series
# method 1
df = pd.DataFrame({'title':series1, 'title2':series2})
# method 2
df = series.to_frame()
# method 3
ser = pd.concat([ser1, ser2], axis = 1)


# creating dataframe from a dictionary
army = pd.DataFrame(raw_data, columns = ['regiment', 'company'])

#change index, inplace changes the original dataset
df.set_index('Part name', inplace=True)
df2 = df.set_index('Part name')

# rename a dataframe using a series
vc_renamed = vc.rename(borough_zip_series)

#slicing the dataframe
df.loc[:, 'school':'guardian']
df.iloc[:,0]

# Transpose
car_table.T

# assign name to categorical variables
df['season'] = df['season'].map({1: 'spring', 2: 'summer', 3: 'fall', 4: 'winter'})
# apply() works on a row / column basis of a DataFrame
# applymap() works element-wise on a DataFrame
# map() works element-wise on a Series.

# Sort the DataFrame by columns
car_table.sort_values(by='unit price', ascending = False)
discipline.sort_values(by = ['Red Cards', 'Yellow Cards'])

# count the number in each category
vc = nyc['Incident Zip'].value_counts()

# count the number of unique items
df['column'].nunique()

# select rows that start with G
df[df['Team'].str.startswith('G')]

# merge dataframe
merged_df = a_df.merge(b_df,
                       left_on= 'column a',
                       right_on= 'column b',
                       #right_index = True
                       suffixes=['_a','_b'])

pd.merge(data1, data2, on='subject_id', how='outer')

# join dataframe (adding more rows)
df = df1.append(df2)
all_data = pd.concat([data1, data2])

# join dataframe/series along columns
all_data_col = pd.concat([data1, data2], axis = 1)

#pivot data
pivoted = pd.pivot_table(df,
                         index=['Complaint', 'BORO'], #gives a hierarchy order
                         columns = 'BORO',
                         values = 'Count',
                         aggfunc=sum,
                         fill_value = 0)

#cross tab
compare = pd.crosstab(result_75['top category'], result_25['top category'])

# create bins
bin=[0,20,25,30,35,40,45,50,55,60,100]
label=['20以下','20-24','25-29','30-34','35-39','40-44','45-49','50-54','55-59','60以上']
df['age_group']=pd.cut(df['age'],bins=bins,labels=label,right=False,include_lowest = True)
#include lowest and exclude highest

# create equally numbered bins
df['quantile'] = pd.qcut(df['ext price'],
                        q=10,
                        labels=labels)


# get only numbers from a column
chipo['item_price'] = [float(value[1:-1]) for value in chipo['item_price']] # strip the dollar sign and trailing space

# Select certain rows based on values
df_new = df.loc[df['url'].isin(unique)]
df_new_neg = df.loc[~df['url'].isin(unique)]


# creating mask
use | for or
use & for and

#Replace missspellings
cars['manufacturer'].replace(['Chevy', 'Chevroelt', 'Toyouta', 'Maxda', 'Vokswagen'],
                             ['Chevrolet', 'Chevrolet', 'Toyota', 'Mazda', 'Volkswagen'])

# delete a column
df = df.drop(['ID','SeniorCitizen','gender'],axis=1)

# add a row based on previous rows
df.loc['growth'] = (df.iloc[0] / df.iloc[1] -1) * 100

```

## Series

```Python
# creating series from a list
unit_prices = [500, 200, 100, 2000, 5000]
part_names = ['Wheels', 'Doors', 'Windows', 'Engine', 'Body']
unit_price_series = Series(unit_prices, index=part_names)

# creating series from dictionaries
obj2 = Series({'Wheels':500, 'Doors':200, 'Windows':100, 'Engine':2000, 'Body':5000})
```

## Groupby
```Python
df.groupby(['title', 'gender'])['rating'].agg(['mean', 'count'])

# Return a dataframe
df.groupby(['Major_category','Major'], as_index=False)['Total'].count()
```

## Time Series
``` Python
# number of days between two dates; with datetime objects
(raw['created_at'].max()-raw['created_at'].min()).days

# count by month/year and plot bar graphs
raw['created_at'].dt.year.value_counts(sort=False).plot(kind = 'bar')
raw['created_at'].dt.month.value_counts(sort=False).plot(kind = 'bar')
raw['created_at'].dt.dayofweek.value_counts(sort=False).plot(kind = 'bar')
raw['created_at'].dt.hour.value_counts().sort_index().plot(kind = 'bar')
raw['created_at'].dt.date.value_counts()[:10]
```
## Miscellaneous
```Python
import os
os.getcwd()
os.chdir(path)

# creating randomn numbers
random = np.random.randint(15000, high=73001, size=398, dtype='l') # high is not inclusive

#upload images
from IPython.display import Image
Image("Freq Plot.png")

# save pictures
savefig('Clustering_1_data/too_many_clusters.png')
