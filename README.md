### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
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

### Program:
```python
import pandas as pd
import matplotlib.pyplot as plt

# Visitor segmentation based on characteristics
# read the data
data = pd.read_csv('clustervisitor.csv')

# Perform segmentation based on characteristics (e.g., age groups)
age_groups = {
    'Children (0-12)': (data['Age'] >= 0) & (data['Age'] <= 12),
    'Teenagers (13-19)': (data['Age'] >= 13) & (data['Age'] <= 19),
    'Young Adults (20-35)': (data['Age'] >= 20) & (data['Age'] <= 35),
    'Adults (36-55)': (data['Age'] >= 36) & (data['Age'] <= 55),
    'Seniors (56+)': (data['Age'] >= 56)
}
visitor_segments = {group: data[condition] for group, condition in age_groups.items()}

# Output the segments
for group, segment_df in visitor_segments.items():
    print(f"--- {group} ---")
    if not segment_df.empty:
        print(f"Number of visitors: {len(segment_df)}")
        print(segment_df.head())
    else:
        print("No visitors in this segment.")

```
### Output:

<img width="383" height="384" alt="image" src="https://github.com/user-attachments/assets/4e12120c-b655-47a0-bf65-f84285f8ac7d" />

### Visualization:
```python
# Create a list to store counts of visitors in each age group
visitor_counts = []

# Count visitors in each age group
for group in visitor_segments:
    visitor_counts.append(len(visitor_segments[group]))
    
# Define age group labels and plot a bar chart
age_group_labels = list(age_groups.keys())

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, visitor_counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```
### Output:

<img width="989" height="587" alt="image" src="https://github.com/user-attachments/assets/938d916b-338c-478f-991b-6b853b86f239" />

### Result:

Hence, Successfully implemented Cluster and Visitor Segmentation for Navigation patterns in Python
