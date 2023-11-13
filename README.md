# ODD2023-Datascience-Ex-04

# MULTIVARIATE ANALYSIS
### AIM:
To perform Multivariate EDA on the given data set.

### EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

### ALGORITHM:
STEP 1:
Import the built-in libraries required to perform EDA and outlier removal.

STEP 2:
Read the given CSV file (titanic dataset).

STEP 3:
Convert the file into a DataFrame and get information about the data.

STEP 4:
Return the objects containing counts of unique values using value_counts().

STEP 5:
Plot the counts in the form of a Histogram or Bar Graph.

STEP 6:
Use Seaborn to view the bar graph comparison of data.

STEP 7:
Find the pairwise correlation of all columns in the DataFrame using dataframe.corr().

STEP 8:
Save the final dataset into the file.

### PROGRAM:
```
Developed By : Niraunjana Gayathri G R
Reg No.      : 212222230096
```
```
CODE:
```
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

dt=pd.read_csv("/content/titanic_dataset.csv")
dt

dt.info()

dt.shape

dt.set_index("PassengerId",inplace=True)

dt

dt.describe()

dt.nunique()

dt['Survived'].value_counts()

per=(dt['Survived'].value_counts()/dt.shape[0]*100).round(2)
per
```

#UNIVARIATE ANALYSIS
```
sns.countplot(data=dt,x="Survived")

fig, ax1 =plt.subplots(figsize=(5,5))
graph=sns.countplot(ax=ax1,x='Survived',data=dt)
graph.set_xticklabels(graph.get_xticklabels(),rotation=90)
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2.,height+0.1,height,ha="center")

dt

dt.Pclass.unique()

dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
```
#BIVARIATE ANALYSIS
```
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)

sns.catplot(x="Survived",hue="Gender",data=dt,kind="count")

fig, ax1 =plt.subplots(figsize=(8,5))
graph=sns.countplot(ax=ax1,data=dt,x='Survived',hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height=p.get_height()
  graph.text(p.get_x()+p.get_width()/2.,height+20.8,height,ha="center")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x=dt["Age"],y=dt["Fare"])

sns.jointplot(x="Age",y="Fare",data=dt)
```
#MULTIVARIATE ANALYSIS
```
fig,ax1 =plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x="Pclass",y="Age",hue="Gender",data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")

g=sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax=g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()-0.01,p.get_height()*1.02,"{0:.1f}".format(p.get_height()),color="red",rotation="horizontal",size="small")
```
##Co-Relation
```
corr=dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
### OUTPUT:
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/b88542f0-65bc-4f87-ac01-d683b23e6fb3)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/0f54a20f-6735-4866-85c7-7d9905d7e632)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/8b861fc6-86db-476e-b78b-cfb198b79c52)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/a41b55e3-2b6b-4c6d-b2f0-d0f6d10d3cfa)
```
Univariate Analysis
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/d6466390-7999-4f6c-91e8-a4c4edda2250)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/fa9c42e9-e925-4809-92fb-c624ef9c4e01)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/db02268f-2592-49d0-8a9a-feb2ee83b203)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/2f24e3f5-2a62-4aca-ab30-f40a13b30b29)
```
Bivariate Analysis
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/43059205-5499-4af3-b131-630d1ad6d195)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/53878468-2645-4972-82e1-24e36ca26a6b)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/1b7485a0-87b3-473a-a4be-32d12f2fb85d)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/4a227f51-2541-4d24-9d10-bf2609093d19)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/5a774761-aa28-45fc-8d99-11f267057efd)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/7fa9a109-55ce-4d51-abed-0126ef8d6b56)
```
Multivariate Analysis
```
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/cfb79950-ed23-4f42-85f8-fa73469a8998)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/0f7e0026-304c-4367-a973-493ec1c2604e)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/165dd4af-3675-44e1-bf0f-06a4699add15)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/49a3d342-9173-442c-9ada-5e104d059cf5)
![image](https://github.com/niraunjana/ODD2023-Datascience-Ex-04/assets/119395610/6e9c1ecf-e433-4060-aaf9-e59c6ae78a60)

### RESULT 
Thus we have read the given dataset and performed multivariate analysis using different kinds of plots


