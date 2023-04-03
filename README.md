## Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
 # Aim:
TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:
Step 1:
Import the required packages(pandas,numpy,scipy)

Step 2:

Read the given csv file

Step3: 

Convert the file into a dataframe and get information of the data.

Step 4:

Remove the non numerical data columns using drop() method.

Step 5:

Detect the outliers in the data set using z scores method.

Step 6:

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

Step 7:

Check if the outliersare removed from data set using graphical methods.

Step 8:

Save the final data set into the file.    
    
## PROGRAM
DEVELOPE BY:D.SWATHI
```
    
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
```

## removing ouliers of bhp.csv file using IQR
```
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
```


## removing ouliers of bhp.csv file using Zscore of 3
```
from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)
```
## Using IQR detect height outliers and print them( height_weight.csv)
```
Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)
```

## Using IQR, detect weight outliers and print them( height_weight.csv)
```
Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```
## OUTPUT

IQR METHOD
df.head()
![image](https://user-images.githubusercontent.com/120440439/227477734-89278911-1b49-4f4a-b3a7-f004a770caed.png)

## df.describe()
![image](https://user-images.githubusercontent.com/120440439/227478049-e32163f6-4123-4519-a1f9-7a22bd087aab.png)

## df.info()

![image](https://user-images.githubusercontent.com/120440439/227486945-570f63c8-ca6f-47e1-aba4-b3dedde51108.png)


## df.shape()

![image](https://user-images.githubusercontent.com/120440439/227478499-3272e60b-7ea3-4b92-a3c5-8340e6f85806.png)

## BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227478859-f2b49f6b-a2e8-4744-83fd-6ee8f3ac77a7.png)

## NEWDATA USING IQR
![image](https://user-images.githubusercontent.com/120440439/227479408-e639703e-4c52-4477-bdab-0182f9d102df.png)

## OUTLIERS
![image](https://user-images.githubusercontent.com/120440439/227479992-94a30505-c540-484e-a1c9-e4ea23f12236.png)

## newdata.shape
![image](https://user-images.githubusercontent.com/120440439/227480653-7e53af85-bbaf-4dff-8b0b-ef5bebb529cc.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![image](https://user-images.githubusercontent.com/120440439/227480885-a2e4146b-0ea3-4af6-b520-d547625231b0.png)

## Zscore of 3

## NEWDATA USING Zscore

![image](https://user-images.githubusercontent.com/120440439/227481262-ea80aeb0-11e2-41d1-b98e-38c860f2c2f8.png)

## OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227481453-59cc2720-7d38-4aad-85cf-d38916778efe.png)

## newdata2.shape
![image](https://user-images.githubusercontent.com/120440439/227481744-0d24c8c3-8e0b-43de-b0a9-8fd947bec4c3.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore

![image](https://user-images.githubusercontent.com/120440439/227482049-96a8fec9-9153-4faf-a5fe-bc6cefb43a40.png)

height_weight.csv

## dataset.shape

![image](https://user-images.githubusercontent.com/120440439/227482339-d03053b0-c9f1-4783-b73b-f6a69fe040ab.png)

## dataset.describe()

![image](https://user-images.githubusercontent.com/120440439/227482687-bf252282-16c2-4ab2-b3ba-d943b7430e33.png)

## dataset.info()

![image](https://user-images.githubusercontent.com/120440439/227482965-3016b0c2-2244-45d5-b5eb-34d07b0b9c7d.png)

## BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227483186-9386e237-a114-4487-b1a5-f437e6a8176a.png)

## HEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227483414-d431c0e0-2363-4e33-b90e-a40f0ed85f84.png)

## DATASET AFTER REMOVING HEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227483664-5168add4-d1be-4958-9d62-9e25e739f6cd.png)

## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227483930-d371b898-632e-4459-ad9e-c0a2147818cb.png) 

## WEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227484118-5d6b886e-c2bf-430e-a6ca-1bd86f0ca862.png)

## DATASET AFTER REMOVING WEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227484376-72993e9e-f5c1-40fa-9c37-c1204c838a91.png)

## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/120440439/227484820-db694c8e-a13c-4dfc-b942-5790064699ea.png)

## RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
