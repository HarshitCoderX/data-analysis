# data-analysis
project performs exploratory data analysis (EDA) on a dataset containing IMDb ratings, genres, and release years of various movies. The goal is to uncover patterns and insights about viewer preferences across genres and time.
import pandas as pd
import matplotlib.pyplot as plt

# 📥 Load the dataset
file_path = r"C:\Users\Anil U R\Downloads\_imbd rating - Sheet1.csv"
df = pd.read_csv(file_path)

# 🔍 Basic Data Overview
print("First 5 rows of the dataset:")
print(df.head())

print("\nDataset Info:")
print(df.info())

print("\nMissing Values:")
print(df.isnull().sum())

print("\nStatistical Summary:")
print(df.describe())

# 📊 IMDb Rating Distribution
plt.figure(figsize=(8, 5))
df['IMDb Rating'].hist(bins=20, edgecolor='black', color='skyblue')
plt.title("Distribution of IMDb Ratings")
plt.xlabel("IMDb Rating")
plt.ylabel("Frequency")
plt.grid(False)
plt.tight_layout()
plt.show()

# 🎭 Genre Frequency
plt.figure(figsize=(10, 6))
df["Genre"].value_counts().plot(kind="bar", edgecolor="black", color='salmon')
plt.title("Genre Frequency")
plt.xlabel("Genre")
plt.ylabel("Count")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# 📈 Average Rating by Year (last 11 years)
print("\nAverage IMDb Rating by Year (last 11 years):")
print(df.groupby("Year")["IMDb Rating"].mean().tail(11))

# 🏆 Average Rating by Genre
print("\nAverage IMDb Rating by Genre:")
print(df.groupby("Genre")["IMDb Rating"].mean().sort_values(ascending=False))
