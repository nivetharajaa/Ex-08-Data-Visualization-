# Ex-08-Data-Visualization-

## AIM

To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation

Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM

### STEP 1

Read the given Data

### STEP 2

Clean the Data Set using Data Cleaning Process

### STEP 3

Apply Feature generation and selection techniques to all the features of the data set

### STEP 4

Apply data visualization techniques to identify the patterns of the data.


# CODE

import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sbn

df=pd.read_csv("/content/Superstore(1).csv",encoding='windows-1252')

df.head()

df.info()

df.isnull().sum()

1.Which Segment has Highest sales?

sbn.barplot(x=df['Segment'],y=df['Sales'])

plt.title("Highest Sales of the segment")

2.Which City has Highest profit?

sbn.barplot(x=df['City'],y=df['Profit'])

plt.title("Highest Profit of cities")

City=df.loc[:,["City","Profit"]]

df.head(5)

City=City.groupby(by=["City"]).sum().sort_values(by="Profit")

plt.figure(figsize=(10,10))

sbn.barplot(x=City.index,y="Profit",data=City)

plt.xticks(rotation = 90)

plt.xlabel=("City")

plt.ylabel=("Profit")

plt.show()

3.Which ship mode is profitable?

sbn.barplot(x=df['Ship Mode'],y=df['Profit'])

plt.title("Profitable Ship Mode")

4.Sales of the product based on region.

sbn.barplot(x=df['Sales'], y=df['Region'])

plt.title("Sales of Product based on Region")

5.Find the relation between sales and profit.

sbn.lineplot(x=df['Sales'], y=df['Profit'])

plt.title("Relation between Sales and Profit")

6.Find the relation between sales and profit based on the following category. i) Segment ii)City iii)States iv)Segment and Ship Mode

v)Segment, Ship mode and Region 

i) Segment

grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

ax.legend()

plt.title("Sales and Profit based on Segment")

plt.show()

2.City

grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('City')

ax.set_ylabel('Value')

ax.legend()

plt.title("Sales and Profit based on City")

plt.show()

3.states

grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('State')

ax.set_ylabel('Value')

ax.legend()

plt.title("Sales and Profit based on States")

4.Segment and Ship Mode

grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])

# Create a bar chart of the grouped data

fig, ax = plt.subplots()

pivot_data.plot(kind='bar', ax=ax)

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

plt.legend(title='Ship Mode')

plt.legend(loc="best")

plt.title("Sales and Profit based on Segment and Ship mode")

plt.show()

5.Segment, Ship mode and Region

grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])

sbn.set_style("whitegrid")

sbn.set_palette("Set1")

pivot_data.plot(kind='bar', stacked=True, figsize=(8, 5))

plt.legend(title='Region')

plt.legend(loc='best')

plt.title("Sales and Profit based on Segment,Ship mode and Region")



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/ee01402a-62ad-420b-8b8b-f632b3d3d5cc)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/4535f575-63e5-4963-8416-b546a4033d90)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/7a37e1a2-2ed1-4fb8-9174-879d30966074)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/9bd392cc-6dc5-4b66-aab8-f16cc3bc471e)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/c1a346ce-a6b6-45eb-9009-68fd4f11f9b6)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/e5bb72f9-4226-45e2-a638-aca63d57a5e7)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/1f06e731-2d36-4031-ba92-48f5fed64e40)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/aa4a61d2-df12-4053-989f-7b8bc9282b77)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/e170b204-d1a7-406a-95a2-bb7f1954b4d7)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/d97717f2-a50f-4765-a6b1-280b16b84b47)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/f3943f3a-dc36-4e9f-861f-97b9f70d59a9)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/df3ad7aa-5f60-4792-90a6-ac685889e28f)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/25237bc4-03a5-4548-9dd7-02a9b350e555)



![image](https://github.com/nivetharajaa/Ex-08-Data-Visualization-/assets/120543388/63818e4c-b36a-4ac4-9b30-ec70169e7f40)




# Result :

Hence the data visualization method for the given dataset applied successfully.



















