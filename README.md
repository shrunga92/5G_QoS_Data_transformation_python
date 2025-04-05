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
# Bandwidth contains 2 units : Kbps and Mbps, where Kbps=1000*Mbps
# Mbps : Convert to Kbps
# Kbps : Leave as it is

def mbps_to_kbps(value):  
    if 'Mbps' in value:
        n = float(value.replace(' Mbps',''))
        return str(n*1000)+' Kbps'
    else:
        return value


df['Required_Bandwidth'] = df['Required_Bandwidth'].map(mbps_to_kbps)
df['Allocated_Bandwidth'] = df['Allocated_Bandwidth'].map(mbps_to_kbps)

df['Required_Bandwidth'] = df['Required_Bandwidth'].str.replace(' Kbps','')
df['Allocated_Bandwidth'] = df['Allocated_Bandwidth'].str.replace(' Kbps','')
df['Latency'] = df['Latency'].str.replace(' ms','')
df['Signal_Strength'] = df['Signal_Strength'].str.replace(' dBm','')
df

```
![image](https://github.com/user-attachments/assets/72d5e645-60e8-4ccb-9760-a14c9bc28974)


``` python
#Convert datatypes 
df['Timestamp'] = pd.to_datetime(df['Timestamp'])
df['User_ID'] = df['User_ID'].astype('int')
df['Application_Type'] = df['Application_Type'].astype('str')
df['Signal_Strength'] = df['Signal_Strength'].astype('int')
df['Latency'] = df['Latency'].astype('int')
df['Required_Bandwidth'] = df['Required_Bandwidth'].astype('float')
df['Allocated_Bandwidth'] = df['Allocated_Bandwidth'].astype('float')
df['Resource_Allocation'] = df['Resource_Allocation'].astype('int')
df.info()
```
![image](https://github.com/user-attachments/assets/02c79674-f56d-4d00-8161-041524bca179)

``` python
df.head(10)
df.tail()

new_df = df
new_df.to_csv("5G_QoS_modified.csv", index=False)
```





