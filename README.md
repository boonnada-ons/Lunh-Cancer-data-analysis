# Introduction
Lung cancer is caused by an error of the DNA in cells of the lungs, which can develop into a tumor and destroy systems in the body.
To predict the potential for lung cancer, the data provide conditions that cause this disease, such as smoking, which is a well-known condition, and others.
The code analyses the data to graph, so it makes it easier to see if any condition affects a lot and causes lung cancer.
# 1.Loading the data from Kaggle
## KaggleHub
KaggleHub is a Python library that provides a simple and consistent way to access and utilize resources (like Models and Datasets) hosted on the Kaggle platform, both within Kaggle Notebooks and in external environments like your Google Colab.
## Usage
``` python
import kagglehub
from kagglehub import KaggleDatasetAdapter
```
## Setting the path to the correct file name
Using the variable ```file_path```
``` python
file_path = "survey lung cancer.csv"
```
## Using function from KaggleHub
uses the ```kagglehub.dataset_load``` function to load a dataset from Kaggle into a pandas DataFrame.
``` python
df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "mysarahmadbhat/lung-cancer",
  file_path,
)
```
```KaggleDatasetAdapter.PANDAS``` specifies that the dataset should be loaded into a pandas DataFrame.

```"mysarahmadbhat/lung-cancer``` is the identifier for the specific dataset on Kaggle.
## Printing the entire DataFrame
print the records by converting the pandas DataFrame into a string
``` python
print("records:", df.to_string())
```

# 2.Creating age groups and filters the data
## os module
```os``` module allows the Python code to interact with the underlying operating system
## Usage
``` python
import os
```
## Checks the existence of directory path
Using the variable ```dataset_directory```
``` python
dataset_directory = '/kaggle/input/lung-cancer'
if os.path.exists(dataset_directory):
    print("Files in the dataset directory:", os.listdir(dataset_directory))
else:
    print(f"Directory not found: {dataset_directory}")
```
If the directory exists, ```print("Files in the dataset directory:", os.listdir(dataset_directory))```

If the directory does not exist, ```print(f"Directory not found: {dataset_directory}")```

# 3.Generating bar charts and pie chart
## counting the number of patients in each condition first
 ```python 

import kagglehub
from kagglehub import KaggleDatasetAdapter
import pandas as pd

file_path = "survey lung cancer.csv"


df = kagglehub.dataset_load(
  KaggleDatasetAdapter.PANDAS,
  "mysarahmadbhat/lung-cancer",
  file_path,
)



df_lung_cancer_filtered = df[df['LUNG_CANCER'] == 'YES'].copy()


condition_cols = ['SMOKING', 'YELLOW_FINGERS', 'ANXIETY', 'PEER_PRESSURE', 'CHRONIC DISEASE', 'FATIGUE ', 'ALLERGY ', 'WHEEZING', 'ALCOHOL CONSUMING', 'COUGHING', 'SHORTNESS OF BREATH', 'SWALLOWING DIFFICULTY', 'CHEST PAIN']



condition_counts = {}
for condition in condition_cols:

    condition_count = df_lung_cancer_filtered[df_lung_cancer_filtered[condition] == 2].shape[0]
    condition_counts[condition] = condition_count


print("Number of lung cancer patients with each condition:")
for condition, count in condition_counts.items():
    print(f"{condition}: {count}")
```
## Making a pie chart of the percentages of number of lung cancer patients with each condition
``` python
import matplotlib.pyplot as plt
import pandas as pd

condition_counts_series = pd.Series(condition_counts)


plt.figure(figsize=(10, 10))
plt.pie(condition_counts_series, labels=condition_counts_series.index, autopct='%1.1f%%', startangle=140)
plt.title('Proportion of Lung Cancer Patients with Each Condition')
plt.axis('equal')
plt.tight_layout()
plt.show()
```

