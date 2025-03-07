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

# Coding and Output:

Read the given Data
```
import pandas as pd
import numpy as np
df = pd.read_csv("C:\\Users\\sudharshan\\Downloads\\Data_set.csv")
df
```
![Screenshot 2025-03-07 152617](https://github.com/user-attachments/assets/a6cd3d11-aff2-4b91-b031-cd42c0621ad2)

 Get the information about the data
```
df.info
```
![Screenshot 2025-03-07 153037](https://github.com/user-attachments/assets/036300f3-c3ee-42c7-a308-4fff34cc738b)

Remove the null values from the data
```
df.dropna(axis=0)
```
![Screenshot 2025-03-07 152700](https://github.com/user-attachments/assets/9f113c0d-87ed-4c00-a7b4-c41491f42e56)



```
df.dropna(axis=1)
```
![Screenshot 2025-03-07 152653](https://github.com/user-attachments/assets/80e2b923-c2de-4b08-ab80-143b826d0fc6)

Save the Clean data to the file
```
df.shape
```
![Screenshot 2025-03-07 152706](https://github.com/user-attachments/assets/89b34b72-1b8e-4f0f-90ae-b53067193b50)

```
df.notnull()
```
![Screenshot 2025-03-07 152717](https://github.com/user-attachments/assets/32e9a5f3-06e8-43a9-9d4a-325bff531933)

```
df.isnull()
```
![Screenshot 2025-03-07 152724](https://github.com/user-attachments/assets/9ed63347-058a-43a4-bb48-d265d8043416)

```
df.isnull().any()
```
![Screenshot 2025-03-07 152641](https://github.com/user-attachments/assets/709c682e-5b56-4aa6-bb7a-3657be7fbb2b)
```
df.dropna("hiii")
```
![image](https://github.com/user-attachments/assets/e293eeb3-161f-4697-bcbd-3d2284357082)

```
df.describe()
```
![Screenshot 2025-03-07 153108](https://github.com/user-attachments/assets/6d8fb618-fd72-4057-b4ce-d2b0baf31d01)

Remove outliers using IQR
```
import pandas as pd
from scipy import stats
import numpy as np

def remove_outliers_iqr(df, numerical_cols):
    Q1 = df[numerical_cols].quantile(0.25)
    Q3 = df[numerical_cols].quantile(0.75)
    IQR = Q3 - Q1
    df_cleaned = df[~((df[numerical_cols] < (Q1 - 1.5 * IQR)) | (df[numerical_cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
    return df_cleaned
df
```
![Screenshot 2025-03-07 153621](https://github.com/user-attachments/assets/d57e8890-e8db-4c53-bf3c-d5c5380bc9a2)

Use zscore of to remove outliers
```
import pandas as pd
from scipy import stats
import numpy as np



def remove_outliers_zscore(df, numerical_cols):
    z_scores = np.abs(stats.zscore(df[numerical_cols], nan_policy='omit'))
    df_cleaned = df[(z_scores < 3).all(axis=1)]
    return df_cleaned
df
```
![Screenshot 2025-03-07 153706](https://github.com/user-attachments/assets/4b29d4a5-9f2c-4a59-a36b-d4aaf6819fa0)









# Result
Thus,we have Read the given Data,Got the information about the data,Removed the null values from the data,Saved the Cleaned data to the file, using IQR and  zscore  to remove outliers

