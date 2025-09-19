### NAME - HARSHITHA V
### REG NO - 212223230074
### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns

### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program - 1:
```python

import pandas as pd
df=pd.read_csv("/content/clustervisitor.csv")
df

cluster = {"Young":(df['Age']<=30),"Middle":((df['Age']>30) & (df['Age']<=50)),"Old":(df['Age']>50)}
print(cluster)

count=[]
for g,c in cluster.items():
  visitors=df[c]
  count.append(len(visitors))
  print(f"visitors in {g} Group")
  print(visitors)
  print(count)

import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.bar(cluster.keys(),count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()

```
### Output:

<img width="403" height="694" alt="image" src="https://github.com/user-attachments/assets/1ded66de-62f7-40ed-b8ed-d66aef31fb52" />







<img width="804" height="561" alt="image" src="https://github.com/user-attachments/assets/3c4b12ad-de1a-4eb6-b8d2-0148261b6de7" />


### Program - 2: 

```python

import pandas as pd
df=pd.read_csv("/content/clustervisitor (Salary).csv")
df

df1=df['Age']
df2=df['Salary']
df3=pd.concat([df1,df2],axis=1)
df3

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans

kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=kmeans.fit_predict(df3)
df3

plt.scatter(df3['Age'],df3['Salary'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Salary')
plt.title('Clustered Data')
plt.show()

```
### Output:
<img width="133" height="616" alt="Screenshot 2025-09-19 111938" src="https://github.com/user-attachments/assets/db7f981d-fb63-4c5f-a5cf-78a366adaf03" />

<img width="637" height="445" alt="Screenshot 2025-09-19 111959" src="https://github.com/user-attachments/assets/fe9a3584-7268-4b7e-a20f-adc22a865b7e" />

### Result:

The implement Cluster and Visitor Segmentation for Navigation patterns in Python is execute successfully.
