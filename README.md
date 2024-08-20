# Exno:1
Data Cleaning Process
# SHAIK MAHAMMAD IMRAAN
# 212223100053
# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm:
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output:
## Data Cleaning:
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![Screenshot 2024-08-20 105832](https://github.com/user-attachments/assets/cc502500-1e06-4b9c-a8aa-b7ef665ef0ef)

```
df.isnull().sum()
```
![Screenshot 2024-08-20 111008](https://github.com/user-attachments/assets/f36c78ab-7c9b-48a4-ac3f-427b27b9aaf8)

```
df.isnull().any()
```
![Screenshot 2024-08-20 111136](https://github.com/user-attachments/assets/2c478196-b344-42e6-8fea-17738951d1b2)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/18c475aa-b7a0-428e-8273-23641baa2143)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/3433c4f3-9178-45e4-b8b5-5b271242ba99)

```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/dc0ed96a-37ef-4000-8331-f79a4b8ad333)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/ce956411-81f4-4f45-9c07-a6fa1bbe58a6)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/15da5cb3-3b2f-445e-a758-83c05c57bac2)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/7da459ae-b31f-45ca-ba60-56b536af2d96)

## IQR(Inter Quartile Range):
```
import pandas as pd
ir=pd.read_csv('/content/iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/519bb2b1-8d6b-402a-b9d0-739a6a1e1237)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/bb167155-e758-448f-8d1a-94a8116d9c47)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/39678f2b-6625-44d7-ab48-7fe54058d56e)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/54d17860-3829-4e64-8f06-c6aa758da18e)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/3bebcdc0-c9b1-4fc4-8f9d-89067d596908)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/b3999232-7877-4171-9e85-ebf3f46e6ea1)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/096e1d91-a7e3-43d1-b656-ee68f3482663)

## Z-Score:
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/af93173a-67ea-4f83-9374-d79f06f59a03)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/6be7abf8-0adc-4d9b-8020-d13f21d810a9)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/661d3847-9cd3-4d0f-9395-b483c849dc59)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/6524cea5-dfdc-417f-bdd4-07fc5acdae34)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/5a2da5cd-6779-4dc7-88b0-c17bc8d204be)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/5b0b7dd5-d77a-4bb5-9adb-16400ceea6d4)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/c672751c-9c06-4712-a6db-a70a5b369fdf)

# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
