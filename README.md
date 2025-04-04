# 5G_QoS_Data_transformation_python
``` python
import pandas as pd
import os

pwd = os.getcwd()

print(f'path is {pwd} now ')

df = pd.read_csv('Quality_of_Service_5G.csv')
df
```
![image](https://github.com/user-attachments/assets/291586f9-41e4-45d4-98b8-fbd50d4abe64)

## 1. Data Pre-Processing :
``` python
df.info()
```

![image](https://github.com/user-attachments/assets/a6833d5a-10ce-4bd9-9a77-01247a25114f)

``` python
df.isna().sum()
```

![image](https://github.com/user-attachments/assets/cdb6be41-dc26-4c9f-a2b0-4e61b980fb62)

``` python
df.duplicated().sum()
```
np.int64(0)

``` python
df['Resource_Allocation'] = df['Resource_Allocation'].str.replace('%','')
df
```
![image](https://github.com/user-attachments/assets/7cf9f352-f297-43ae-b374-c1ff6a86542c)

``` python
df['User_ID'] = df['User_ID'].str.replace('User_','')
df
```

![image](https://github.com/user-attachments/assets/9b5931b2-e01e-43d8-9ed5-44c7e60d7e55)


``` python

```



``` python

```


``` python

```

``` python

```

``` python

```

``` python

```



