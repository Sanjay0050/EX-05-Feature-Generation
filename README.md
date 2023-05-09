# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE

```

# Data.csv
```
import pandas as pd
df=pd.read_csv("data.csv")
df

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder

oe=OrdinalEncoder()
df1=df.copy()

df1["City"] = oe.fit_transform(df1[["City"]])
df1["bin_1"] = oe.fit_transform(df1[["bin_1"]])
df1["Ord_1"] = oe.fit_transform(df1[["Ord_1"]])
df1["Ord_2"] = oe.fit_transform(df1[["Ord_2"]])
df1["bin_2"] = oe.fit_transform(df1[["bin_2"]])

df2=df.copy()

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```
# Encoding.csv
```
import pandas as pd
qf=pd.read_csv("encoding.csv")
qf

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
from sklearn.preprocessing import OneHotEncoder

oe=OrdinalEncoder()

qf1=qf.copy()


qf1["bin_1"] = oe.fit_transform(qf1[["bin_1"]])
qf1["nom_0"] = oe.fit_transform(qf1[["nom_0"]])
qf1["ord_2"] = oe.fit_transform(qf1[["ord_2"]])
qf1["bin_2"] = oe.fit_transform(qf1[["bin_2"]])

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
qf0=pd.DataFrame(sc.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf0   

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
qf2=pd.DataFrame(sc1.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
qf3=pd.DataFrame(sc2.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
qf4=pd.DataFrame(sc3.fit_transform(qf1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
qf4
```

# Titanic_dataset.csv
```
import pandas as pd
rf=pd.read_csv("titanic.csv")
rf

#removing unwanted data
rf.drop("Name",axis=1,inplace=True)
rf.drop("Ticket",axis=1,inplace=True)
rf.drop("Cabin",axis=1,inplace=True)  

rf["Age"]=rf["Age"].fillna(rf["Age"].median())
rf["Embarked"]=rf["Embarked"].fillna(rf["Embarked"].mode()[0])

rf.isnull().sum()

rf1=rf.copy()

from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
oe=OrdinalEncoder()

e1=OrdinalEncoder(categories=[embark])
rf1['Embarked'] = e1.fit_transform(rf[['Embarked']])
rf1['Sex'] = oe.fit_transform(rf[['Sex']])
rf1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
rf0=pd.DataFrame(sc.fit_transform(rf1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
rf0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
rf3=pd.DataFrame(sc1.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
rf4=pd.DataFrame(sc2.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
rf5=pd.DataFrame(sc3.fit_transform(rf1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
rf5
```


# OUPUT

# Data.csv:

## Initial dataset:
![image](https://user-images.githubusercontent.com/94154683/195382314-da5fb872-3a3d-44c3-8ce7-bf67d43cf0b5.png)
## Encoded dataset:
![image](https://user-images.githubusercontent.com/94154683/195382454-55bad3fd-9bd4-4757-9b95-2449339e4f48.png)
## Data scaling using MinMaxScaler:
![image](https://user-images.githubusercontent.com/94154683/195383188-b5f40ae9-024e-41f5-8d44-91d1bf2b85ec.png)
## Data scaling using StandardScalar:
![image](https://user-images.githubusercontent.com/94154683/195383387-c6589430-a167-4c24-8691-11cd678f7e1d.png)
## Data scaling using MaxAbsScaler:
![image](https://user-images.githubusercontent.com/94154683/195383566-8d71b77a-1bbc-41e0-98c2-adfac5381e2c.png)
## Data scaling using RobustScaler:
![image](https://user-images.githubusercontent.com/94154683/195383775-c51d2824-3daa-4372-ba91-4ce9c5dd0efd.png)

# Encoding.csv:

## Initial dataset:
![image](https://user-images.githubusercontent.com/94154683/195384264-b69a805d-7e71-4184-ae7d-ba6f17347235.png)
## Encoded dataset:
![image](https://user-images.githubusercontent.com/94154683/195384331-19f451cf-6040-4d2c-bd13-d08a672f795d.png)
## Data scaling using MinMaxScaler:
![image](https://user-images.githubusercontent.com/94154683/195384504-49708c6f-c212-45dd-99ee-43aff50d4099.png)
## Data scaling using StandardScalar:
![image](https://user-images.githubusercontent.com/94154683/195384567-5414cd57-52cc-4c86-95ab-460f1cfcf9d8.png)
## Data scaling using MaxAbsScaler:
![image](https://user-images.githubusercontent.com/94154683/195384624-aae7880e-f57f-4193-a9e0-9c7961543448.png)
## Data scaling using RobustScaler:
![image](https://user-images.githubusercontent.com/94154683/195384688-9f6a64b3-2640-4b59-ab35-1bc14e7a2b82.png)

# Titanic_dataset.csv:

## Initial dataset:
![image](https://user-images.githubusercontent.com/94154683/195384954-54e7d199-0ea2-4048-ad19-5eed3b134ef8.png)
## isnull.sum()
![image](https://user-images.githubusercontent.com/94154683/195385077-5d978b8f-062a-498f-bf4a-e67f6863f8ca.png)
## Encoded dataset:
![image](https://user-images.githubusercontent.com/94154683/195385213-4a57ef5d-67b0-4057-97f6-3d64a56d5a7c.png)
## Data scaling using MinMaxScaler:
![image](https://user-images.githubusercontent.com/94154683/195385326-ebb49de1-1e06-45b2-a7c0-bc03e35d01c2.png)
## Data scaling using StandardScalar:
![image](https://user-images.githubusercontent.com/94154683/195385448-12310dbc-1ece-4ecb-9f15-f45e14fa737a.png)
## Data scaling using MaxAbsScaler:
![image](https://user-images.githubusercontent.com/94154683/195385537-beb28e3e-a11a-446a-bd96-a3aa9463b701.png)
## Data scaling using RobustScaler:
![image](https://user-images.githubusercontent.com/94154683/195385597-f8f77764-76c2-497e-b1fe-dd26db2077ed.png)


# RESULT:
Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully.

