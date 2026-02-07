### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07-02-2026
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

### Program 1:
```python

import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("clustervisitor.csv")
cluster = {"young" : (df['Age'] <= 30) , "middle" : (df['Age'] > 30) & (df['Age'] <= 50) , "old" : (df['Age'] > 50)}
count = []
count = []

for group, condition in cluster.items():
    visitors = df[condition]
    count.append(len(visitors))

    print(f"Visitors in {group} age are:\n")
    print(visitors)
    print(f"\nTotal visitors in {group}: {len(visitors)}")
    print("-" * 40)

plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(), count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()

```
### Output:

<img width="391" height="772" alt="image" src="https://github.com/user-attachments/assets/34edee66-0ee4-4cab-9d9d-c863343844ba" />


<img width="840" height="560" alt="image" src="https://github.com/user-attachments/assets/e06e45d4-e11c-4c7c-8508-8638346abef2" />




### Program 2:
```python
# Create a list to store counts of visitors in each age group
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age'] 
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3


import matplotlib.pyplot as plt 
plt.figure(figsize=(8, 6))
plt.scatter(x=df3['Age'],y=df3['Income'], c=df3 ['cluster'])
plt.xlabel('Age')
plt.ylabel ('Income')
plt.title('Visitor Distribution in Different Clusters')
plt.show()
             
```
### Output:


<img width="745" height="906" alt="image" src="https://github.com/user-attachments/assets/a099177e-a920-4b4b-ab6f-0cc83748711d" />



<img width="724" height="518" alt="image" src="https://github.com/user-attachments/assets/7b9523c0-114b-41e0-85c3-73b2925959b9" />



### Result:

Thus, cluster and Visitor Segmentation for Navigation patterns have been implemented successfully.
