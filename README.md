Task 1

# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the Iris dataset from seaborn
try:
    # Load dataset
    iris = sns.load_dataset('iris')
    print("Dataset loaded successfully!")

    # Display the first few rows
    print("First 5 rows of the dataset:")
    print(iris.head())

    # Check data types and missing values
    print("\nDataset Info:")
    print(iris.info())

    # Check for missing values
    print("\nMissing values in each column:")
    print(iris.isnull().sum())

except FileNotFoundError:
    print("Error: Dataset not found.")
except Exception as e:
    print(f"An error occurred: {e}")

# No missing values in this dataset. If there were, we could handle them like this:
# iris.fillna(method='ffill', inplace=True) or iris.dropna(inplace=True)


Task 2

# Compute basic statistics
print("\nBasic Statistics:")
print(iris.describe())

# Grouping data by species and computing the mean of numerical columns
print("\nMean values grouped by species:")
print(iris.groupby('species').mean())

# Observations
print("\nObservations:")
print("1. The setosa species tends to have smaller petal length and width compared to the others.")
print("2. Versicolor and virginica have larger sepal lengths on average.")


Task 3
Line chart
# Line chart showing trends of petal length for the first 10 samples
plt.figure(figsize=(10, 6))
plt.plot(iris.index[:10], iris['petal_length'][:10], marker='o', label='Petal Length')
plt.title("Trend of Petal Length for the First 10 Samples")
plt.xlabel("Index")
plt.ylabel("Petal Length (cm)")
plt.legend()
plt.grid()
plt.show()

Bar chart

# Bar chart showing average petal length by species
plt.figure(figsize=(10, 6))
iris.groupby('species')['petal_length'].mean().plot(kind='bar', color=['red', 'green', 'blue'])
plt.title("Average Petal Length by Species")
plt.xlabel("Species")
plt.ylabel("Average Petal Length (cm)")
plt.show()

Histogram

# Histogram of petal length
plt.figure(figsize=(10, 6))
plt.hist(iris['petal_length'], bins=15, color='purple', edgecolor='black')
plt.title("Distribution of Petal Length")
plt.xlabel("Petal Length (cm)")
plt.ylabel("Frequency")
plt.show()

Scatter plot

# Scatter plot of sepal length vs. petal length
plt.figure(figsize=(10, 6))
sns.scatterplot(x='sepal_length', y='petal_length', hue='species', data=iris)
plt.title("Sepal Length vs. Petal Length by Species")
plt.xlabel("Sepal Length (cm)")
plt.ylabel("Petal Length (cm)")
plt.legend(title='Species')
plt.show()
