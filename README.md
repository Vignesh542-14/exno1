# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
 ```
import pandas as pd
exp=pd.read_csv("/content/SAMPLEIDS.csv")
exp
```
![image](https://github.com/user-attachments/assets/d1ea16aa-8d1d-4c09-97ff-e8b56fbb9c65)
```
exp.isnull().sum()
```
![image](https://github.com/user-attachments/assets/35efff63-a231-4bc4-9019-5084e8994542)
```
exp.isnull().any()
```
![image](https://github.com/user-attachments/assets/a258f4c7-5a32-42bb-9b2f-20eae7174f7f)
```
exp.dropna()
```
![image](https://github.com/user-attachments/assets/58e44e4f-050a-4cbe-ad85-eeb730b081e0)
```
exp.fillna(0)
```
![image](https://github.com/user-attachments/assets/1f122b81-7d12-4b48-b53c-b28cf0751229)
```
exp.fillna(method="ffill")
```
![image](https://github.com/user-attachments/assets/99ba2248-3cd5-4535-85b2-06a1beeeb2ef)
```
exp.fillna(method="bfill")
```
![image](https://github.com/user-attachments/assets/c19b280e-fbfc-4b46-9b25-de2dfd657290)
```
exp_dropped=exp.dropna()
exp_dropped
```
![image](https://github.com/user-attachments/assets/d0904eb5-cca4-4e41-9c1d-5970f8bf8179)
```
exp.fillna({'NAME':'MOHAN','GENDER':'MALE','ADDRESS':'THIRUVOTTIYUR','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
# IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/01408a64-3a0d-4544-beb2-8922bfec4d78)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/2a600f5d-78f8-47e0-8ca0-c6f2b1c8f2bb)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/f0768ccd-01de-4294-86cc-7c1b8cd664e1)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
![image](https://github.com/user-attachments/assets/0cc1f28b-b9ad-4ddc-a8a0-00b7f93ff2c3)
```
outlier=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
outlier['sepal_width']
```
![image](https://github.com/user-attachments/assets/2c99664f-9b59-45f3-87ad-afc68479d2ac)
```
o=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
print(o)
```
![image](https://github.com/user-attachments/assets/c3fbe723-e087-4e15-b4a9-a4d9424273a1)
```
sns.boxplot(x='sepal_width',data=o)
```
![image](https://github.com/user-attachments/assets/2e47619b-6e15-4e84-87fb-ae4a88d28562)

# Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
data_set=pd.read_csv("/content/heights.csv")
data_set
```
![image](https://github.com/user-attachments/assets/34898518-2406-46ad-9d6c-00f923f1aabb)
```
z=pd.read_csv("/content/heights.csv")
q1=z['height'].quantile(0.25)
q2=z['height'].quantile(0.50)
q3=z['height'].quantile(0.75)
iqr=q3-q1
print(iqr)
```
![image](https://github.com/user-attachments/assets/4fddcf03-243f-4c05-9904-18592fb291f7)
```
low = q1-1.5*iqr
print(low)
```
![image](https://github.com/user-attachments/assets/1f0952f9-44e5-4f3e-8f93-7ac65452776a)
```
high = q3+1.5*iqr
print(high)
```
![image](https://github.com/user-attachments/assets/f8e9afaf-4c12-4da9-945e-9b4c65df110b)
```
z1=z[((z['height']>=low)&(z['height']<=high))]
z1
```
![image](https://github.com/user-attachments/assets/7a29e91a-448d-43e9-843e-1f21f71c1a3a)
```
z=np.abs(stats.zscore(z['height']))
z
```
![image](https://github.com/user-attachments/assets/ae8c6a1f-006e-41b0-b4b9-877f9680b2f6)
```
z1=z[z<3]
z1
```
![image](https://github.com/user-attachments/assets/9f7cd7fc-bc42-4538-8ffc-1d2e4f9d2caf)
```

# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
