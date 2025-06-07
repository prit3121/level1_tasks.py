# level1_tasks.py
Internship project completed level 1 at Cognifyz Technologies involving data analysis tasks in Python.
#Level 1
#Task 1
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("C:/Users/priya/Downloads/Cleaned_Dataset.csv")

# Clean the data: Drop rows where 'Cuisines' is missing
df_clean = df.dropna(subset=['Cuisines'])

# Split multiple cuisines per row
cuisine_series = df_clean['Cuisines'].str.split(',').explode().str.strip()

# Count most frequent cuisines
cuisine_counts = cuisine_series.value_counts()

# Top 3 cuisines
top_3_cuisines = cuisine_counts.head(3)
print("Top 3 Cuisines:\n", top_3_cuisines)

# Calculate percentage
total_restaurants = len(df_clean)
top_3_percent = (top_3_cuisines / total_restaurants) * 100
print("\nPercentage of Restaurants Serving Top 3 Cuisines:\n", top_3_percent.round(2))

# Plotting
top_3_cuisines.plot(kind='bar', color='purple')
plt.title("Top 3 Cuisines")
plt.xlabel("Cuisine")
plt.ylabel("Number of Restaurants")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
