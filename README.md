# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

## Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

## ALGORITHM

### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


## CODE

```
**Feature Generation - Encoding Data.csv**

import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/Encoding Data.csv")
df1 = df.copy()
df1.head(5)
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
climate = ['Cold','Warm','Hot']
enc = OrdinalEncoder(categories = [climate])
enc.fit_transform(df1[["ord_2"]])
df1['Ord_2'] = enc.fit_transform(df1[["ord_2"]])
df1.head(5)
df2 = df1.copy()
le = LabelEncoder()
df2['Nom_0'] = le.fit_transform(df2[["nom_0"]])
df2.head(5)
df3 = df2.copy()
from category_encoders import BinaryEncoder
be = BinaryEncoder()
data = be.fit_transform(df['bin_1'])
df3  = pd.concat([df,data],axis=1)
df3.head(5)
df4 = df3.copy()
from category_encoders import BinaryEncoder
be1 = BinaryEncoder()
newdata = be.fit_transform(df['bin_2'])
df4  = pd.concat([df,newdata],axis=1)
df4.head(5)
df['ord_2'] = le.fit_transform(df['ord_2'])
sbn.set(style ="darkgrid")
sbn.countplot(df['ord_2'])


**Feature Generation - data.csv**

import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/data.csv")
df.head(5)
df.info()
df.isnull().sum()
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
df['Ord_2'] = le.fit_transform(df['Ord_2'])
sbn.set(style ="darkgrid")
sbn.countplot(df['Ord_2'])
from sklearn.preprocessing import OneHotEncoder
enc = OneHotEncoder()
enc = enc.fit_transform(df[['City']]).toarray()
encoded_colm = pd.DataFrame(enc)
df = pd.concat([df, encoded_colm], axis=1)
df = df.drop(['City'], axis=1)
df.head(10)
df = pd.get_dummies(df, prefix=['Ord_2'], columns=['Ord_2'])
df.head(10)
df = pd.get_dummies(df, prefix=['Ord_1'], columns=['Ord_1'])
df.head(10)


**Feature Generation - titanic_dataset.csv**

import pandas as pd
import numpy as np
import seaborn as sbn
df = pd.read_csv("/content/titanic_dataset.csv")
df.head(5)
df.info()
df.isnull().sum()
df['Age']=df['Age'] . fillna(df['Age'].mean())
df['Cabin']=df['Cabin']. fillna(df['Cabin']. mode() [0])
df['Embarked']=df['Embarked'] . fillna(df['Embarked'].mode( )[0])
df.isnull().sum()
from sklearn.preprocessing import LabelEncoder
lc = LabelEncoder()
df['Sex'] = lc.fit_transform(df['Sex'])
sbn.set(style ="darkgrid")
sbn.countplot(df['Sex'])
from sklearn.preprocessing import OneHotEncoder
enc= OneHotEncoder()
enc= enc.fit_transform(df[['Name']]).toarray()
encoded_colm = pd.DataFrame(enc)
df= pd.concat([df, encoded_colm], axis=1)
df= df.drop(['Name'], axis=1)
df.head(10)
df = pd.get_dummies(df, prefix=['Ticket'] ,columns=['Ticket'])
df.head(10)
df = pd.get_dummies(df, prefix=['Embarked'] ,columns=['Embarked'])
df.head(10)

```

## OUPUT

### Feature Generation - Encoding Data.csv

![image](https://user-images.githubusercontent.com/119560261/232685501-6b3af4df-8ed6-44de-b4f8-5fa81dfecea4.png)
![image](https://user-images.githubusercontent.com/119560261/232685724-36b05934-b9c3-404c-aa43-8f5bcde8955c.png)
![image](https://user-images.githubusercontent.com/119560261/232685803-85e56ee9-4889-4f9a-90a7-e374a8de8f47.png)

### Feature Generation - data.csv

![image](https://user-images.githubusercontent.com/119560261/232686446-3f1cf39b-565d-4f8f-9fe0-4b2c0f0abff3.png)
![image](https://user-images.githubusercontent.com/119560261/232686516-d4a831d0-ed70-4415-9eb2-4d0a2e10f1bf.png)
![image](https://user-images.githubusercontent.com/119560261/232686666-1eadb458-c5a1-4e85-8a21-6a371ae50936.png)
![image](https://user-images.githubusercontent.com/119560261/232686811-a8c4a8b7-2b5b-4271-8f9b-e67ca185d424.png)

### Feature Generation - titanic_dataset.csv

![image](https://user-images.githubusercontent.com/119560261/232686975-9bbd1a8f-57da-404c-a521-bffa08761bd6.png)
![image](https://user-images.githubusercontent.com/119560261/232687057-f7298af2-da33-44ed-899f-e07fd034d296.png)
![image](https://user-images.githubusercontent.com/119560261/232687117-79c52972-7d28-479a-88ae-e845eeaffe96.png)
![image](https://user-images.githubusercontent.com/119560261/232687286-d51127f2-2409-4071-8591-92fe152625ff.png)

## RESULT:
Thus the Feature Generation for the given datasets had been executed successfully
