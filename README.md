





# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
    
# Aim:
TO detect and remove the outliers in the given data set and save the final data.

# ALGORITHM:
# STEP 1:
Read the given Data.

# STEP 2:
Get the information about the data.

# STEP 3:
Detect the Outliers using IQR method and Z score.

# STEP 4:
Remove the outliers.

# STEP 5:
Plot the datas using Box Plot.
 
## PROGRAM:

DEVELOPED BY: ARUN KUMAR SUKDEV CHAVAN


REGISTER NUMBER: 212222230013
```python
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
``

### removing ouliers of bhp.csv file using IQR
```python
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
### removing ouliers of bhp.csv file using Zscore of 3
```python
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

### Using IQR detect height outliers and print them( height_weight.csv)
```python
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

### Using IQR, detect weight outliers and print them( height_weight.csv)
```python
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
# OUTPUT:
# bhp.csv IQR METHOD
## df.head():
![Screenshot 2023-03-27 103203](https://user-images.githubusercontent.com/120380280/227845266-fb3eb085-b1d4-4282-bd63-519f0d355d89.png)
## df.describe():
![Screenshot 2023-03-27 103354](https://user-images.githubusercontent.com/120380280/227845462-accbc6e3-0546-4f4f-82aa-728225d351ca.png)
## df.info():
![Screenshot 2023-03-27 103502](https://user-images.githubusercontent.com/120380280/227845630-61cc97cb-be05-463a-8d54-202287a8921b.png)
## df.shape:
![Screenshot 2023-03-27 103636](https://user-images.githubusercontent.com/120380280/227845837-d6d5860c-4174-4e2b-aa1d-ed5db1f8d126.png)

### BOXPLOT BEFORE REMOVING OUTLIERS:
![Screenshot 2023-03-27 103755](https://user-images.githubusercontent.com/120380280/227846021-48581513-ee06-49f6-beb2-a884a9ab9257.png)
### NEWDATA USING IQR:
![Screenshot 2023-03-27 103957](https://user-images.githubusercontent.com/120380280/227846304-61d61dcf-779c-4a3c-856c-0e56a5c4d1ef.png)
## OUTLIERS:
![Screenshot 2023-03-27 104156](https://user-images.githubusercontent.com/120380280/227846544-46fb48a3-23e7-45a5-bed3-00b275fc6e54.png)
## Newdata.shape:
![Screenshot 2023-03-27 104301](https://user-images.githubusercontent.com/120380280/227846652-eb20f15c-97f3-49a1-b53d-4445610288e0.png)
### BOXPLOT AFTER REMOVING OUTLIERS USING IQR:
![Screenshot 2023-03-27 104354](https://user-images.githubusercontent.com/120380280/227846785-efcb64ee-bb72-4fc4-9908-6380ffa093e0.png)
## Zscore of 3
### NEWDATA USING Zscore:
![Screenshot 2023-03-27 104524](https://user-images.githubusercontent.com/120380280/227846947-74db3928-a013-40cc-b00e-bce0c1540b1c.png)
## OUTLIERS:
![Screenshot 2023-03-27 104633](https://user-images.githubusercontent.com/120380280/227847091-3eef7992-59f4-4548-9e70-ea65b2108222.png)
## Newdata2.shape:
![Screenshot 2023-03-27 104633](https://user-images.githubusercontent.com/120380280/227847202-0db42743-bb53-4a2a-b871-348c9b123f75.png)
# BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:
![Screenshot 2023-03-27 104814](https://user-images.githubusercontent.com/120380280/227847310-8ccfa6d2-6d82-4ba8-b0c6-08ac3aace1ef.png)
# height_weight.csv
# dataset.shape:
![Screenshot 2023-03-27 105047](https://user-images.githubusercontent.com/120380280/227847640-99a6cfaf-499f-4866-8e48-41f382fa53fd.png)
# dataset.describe():
![Screenshot 2023-03-27 105209](https://user-images.githubusercontent.com/120380280/227847834-a9be60bc-bc03-4efd-9681-9b70fe351ae6.png)
# dataset.info():
![Screenshot 2023-03-27 105302](https://user-images.githubusercontent.com/120380280/227847954-e4ba3e46-d673-4b06-b47d-6aafe051c33e.png)
# BOXPLOT BEFORE REMOVING OUTLIERS:
![Screenshot 2023-03-27 105356](https://user-images.githubusercontent.com/120380280/227848079-f064aa70-02c7-4f44-b01a-da4b9142d2b0.png)
# HEIGHT OUTLIERS:
![Screenshot 2023-03-27 105445](https://user-images.githubusercontent.com/120380280/227848191-9a3fdbb6-8100-426a-93be-73f2d1b7b8bc.png)
# DATASET AFTER REMOVING HEIGHT OUTLIERS:
![Screenshot 2023-03-27 105529](https://user-images.githubusercontent.com/120380280/227848402-775c22a7-6b84-4814-936f-c49e19340582.png)
# BOXPLOT AFTER REMOVING HEIGHT OUTLIERS:
![Screenshot 2023-03-27 110005](https://user-images.githubusercontent.com/120380280/227848966-686a12ee-d86c-42fe-adf2-ea8325c79cdb.png)
# WEIGHT OUTLIERS:
![Screenshot 2023-03-27 110041](https://user-images.githubusercontent.com/120380280/227849067-2596576e-e1cf-497d-acdf-ec161f7ab294.png)
# DATASET AFTER REMOVING WEIGHT OUTLIERS:
![Screenshot 2023-03-27 110130](https://user-images.githubusercontent.com/120380280/227849186-8c5d1e15-7995-4960-ae62-047d0026d84a.png)
# BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:
![Screenshot 2023-03-27 110237](https://user-images.githubusercontent.com/120380280/227849322-d1a2676e-9f1b-4845-9b7a-875cee529dbc.png)
# RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
