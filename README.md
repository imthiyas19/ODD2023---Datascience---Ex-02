## Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## ALGORITHM:
# STEP 1:
Read the given Data.

# STEP 2:
Get the information about the data.

# STEP 3:
Detect the Outliers using IQR method and Z score.

# STEP 4:
Remove the outliers:

# STEP 5:
Plot the datas using box plot.

## PROGRAM:
```
DEVELOPED BY: MOHAMMED IMTHIYAS.M
REGISTER NUMBER: 212222230083

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### Removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)
#New dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### Removing ouliers of bhp.csv file using Zscore of 3

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

### Using IQR detect height outliers and print them( height_weight.csv)

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


### Using IQR, detect weight outliers and print them( height_weight.csv)

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
OUTPUT:

df.head():

![273361464-83981ba8-fd6c-4e87-b548-861a2b589886](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/a38f0c90-b218-4eda-9cf3-4548f63e5d1a)



 df.describe():

![273361481-0bae0a39-d9e5-4cc0-89b7-c0b2adedfc63](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/73f9fdbf-a566-4d3c-85fa-7367dedd3b77)


 

 df.info():

![273361499-2c0c5a3d-c536-43c5-9ecb-df1d6ae10238](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/a6bda8ea-656d-4145-916a-7029545f85b2)


 



df.shape:

![273361526-34298bd7-a38b-4dd8-b086-c110f8c754e5](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/aba0ede8-e4e3-4915-b140-b7829b9b35a1)



BOXPLOT BEFORE REMOVING OUTLIERS:

![273361553-65c4c528-4ee3-4ebd-8737-5548a2248217](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/da47072e-7bba-4457-ae52-1d38b1e71e04)






NEWDATA USING IQR:

![273361567-10e5520c-28a4-407f-adad-9c25c1bc8f7d](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/8559b00b-02c0-4d38-9e15-8f76d7d7df44)





OUTLIERS:


![273361581-90d7da5c-a431-4642-8689-9dbbbe0c0573](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/de8c5d83-8701-4c0d-9cc8-c71d3d183825)





newdata.shape:
![273361599-8e87d4c7-e38e-43a3-b974-64d14147019d](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/295b3e01-a49b-4a3c-acc8-87e798509d8b)


BOXPLOT AFTER REMOVING OUTLIERS USING IQR:

![273361622-c21729d1-299f-4f9d-a93b-d170a22350ff](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/5e47578d-98c5-4286-9580-794513870369)




Zscore of 3: NEWDATA USING Zscore:
![273361651-ff03d0ac-bb5c-43f5-8b92-987e06cce3ed](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/463375f5-7c3f-4a18-9482-6a43fd18af1a)



OUTLIERS:



![273361808-326018ff-c570-435a-97f1-fc01b5ee730a](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/3865d914-c729-49af-9364-85589aec58b5)




newdata2.shape:


![273361825-32550c1e-e779-42d1-9754-9a8c4e14c71a](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/e0f35492-36d3-487a-965a-5f3f1adf29ae)



BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:
![273361841-13f51c6a-ab0a-4378-848d-b128a57e809a](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/16693454-0ab5-4d50-ab69-1e907ce0e6f3)




height_weight.csv:


![273361846-acc920ec-07ea-4be8-a3e2-a3af45116461](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/f66b7a10-3d6f-4a05-b884-f9f46569aafb)



dataset.describe():
![273361858-a654e7bb-ca23-427e-8ac0-71549493ecca](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/7a19529b-6ab7-4c39-abe6-c24a6d6e3e4b)


dataset.info():


![273361872-dc7661be-39f4-40fd-a081-38bec3c986f1](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/21887d5f-5c4e-4eda-800d-d070d3e7be20)



BOXPLOT BEFORE REMOVING OUTLIERS:


![273361895-a584737a-2709-4e42-870a-8d2d8fdf3e1c](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/e68c3a9b-6c0c-47b8-9ec7-c36fed0a8b49)






HEIGHT OUTLIERS:


![273361908-3c9192df-424c-4d9d-960c-6a40d60988f0](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/82a76878-5146-435f-97a3-8bcfda4449dd)





DATASET AFTER REMOVING HEIGHT OUTLIERS:



![273361922-c21f2f5f-1757-48c9-bb33-6a00bb2669cc](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/e56942c4-9937-46c3-92b3-1c7981169e81)



BOXPLOT AFTER REMOVING HEIGHT OUTLIERS:

![273361942-bab55de5-0dce-4f29-9e9b-6bb88937f371](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/045df6c5-30fd-4474-97ae-bd35371afabe)


WEIGHT OUTLIERS:


![273361955-f5d18c77-583f-4365-85f0-bef27c5f47af](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/7b2aa3ef-beff-47d3-874a-9ffceff8c49c)



DATASET AFTER REMOVING WEIGHT OUTLIERS:



![273361992-0944b001-897f-4256-a907-9254784740dd](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/55f12252-55dd-443e-93a0-f2971c82e3ad)



BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:
![image](https://github.com/imthiyas19/ODD2023---Datascience---Ex-02/assets/120353416/0dbd1944-eff6-43e5-be47-4674a021f1a3)



RESULT:

The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
