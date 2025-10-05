# Introduction
Lung cancer is caused by an error of the DNA in cells of the lungs, which can develop into a tumor and destroy systems in the body.
To predict the potential for lung cancer, the data provide conditions that cause this disease, such as smoking, which is a well-known condition, and others.
The code analyses the data to graph, so it makes it easier to see if any condition affects a lot and causes lung cancer.
# 1.loading the data from Kaggle
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
# 3.Generating bar charts and pie chart
