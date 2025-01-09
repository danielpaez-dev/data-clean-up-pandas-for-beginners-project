# Final prework project - Step by step solution
## Let's Start Solving the Exercises

**Exercise 00: Basic Declarations**
```python
# Your name, as a string
name = "Your Name"

# Your age, as an integer
age = 30

# Do you like programming? As a boolean
likes_programming = True

# Your average grade, as a float
average_grade = 8.5

# List of favorite numbers
favorite_numbers = [3, 7, 11, 13, 17]

# Student information as a dictionary
student = {
    "name": "Alice",
    "age": 22,
    "final_grade": 9.2
}
```


**Exercise 01: Basic Data Analysis**
```python

# List of grades
grades = [8.5, 9.2, 7.8, 8.9, 10]

# Calculate average
average = sum(grades) / len(grades)
print("Average grade:", average)

# Find highest and lowest grades
highest_grade = max(grades)
lowest_grade = min(grades)
print("Highest grade:", highest_grade)
print("Lowest grade:", lowest_grade)
```
### Real estate data cleaning with Pandas for efficient analysis

**Example: Loading and Exploring the Dataset**
```python
import pandas as pd

# Load the CSV data
df = pd.read_csv('assets/real_estate.csv', sep=';')

# Show the first 5 rows
print(df.head())
```

**Exercise 01: What is the most expensive house in the entire dataset?**
```python
# Find the most expensive house
most_expensive = df.loc[df['price'].idxmax()]
print("The most expensive house is located at", most_expensive['url_inmueble'], "and its price is", most_expensive['price'])
```

**Exercise 02: What is the cheapest house in the dataset?**
```python
# Find the cheapest house
cheapest_house = df.loc[df['price'].idxmin()]

# Print the address and price
print("The cheapest house is located at", cheapest_house['url_inmueble'], "and its price is", cheapest_house['price'])
```

**Exercise 03: What is the largest and smallest house in the dataset?**
```python
# Find the largest house by surface area
largest_house = df.loc[df['surface'].idxmax()] 

# Find the smallest house by surface area
smallest_house = df.loc[df['surface'].idxmin()]

# Print the results
print("The largest house is located at", largest_house['url_inmueble'], "and its surface area is", largest_house['surface'], "square meters.")
print("The smallest house is located at", smallest_house['url_inmueble'], "and its surface area is", smallest_house['surface'], "square meters.") 
```

**Exercise 04: How many unique populations are in the dataset?**
```python
# Find unique populations
unique_populations = df['level5'].unique()

# Count the number of unique populations
num_populations = len(unique_populations)

# Print the number of unique populations
print("Number of unique populations:", num_populations)

# Print the names of the populations
print("Populations:", ", ".join(unique_populations))
```

**Exercise 05: Does the dataset contain null values (NAs)?**
```python
# Check for null values in the entire DataFrame
has_null_values = df.isnull().any().any() 

# Find columns with null values
columns_with_nulls = df.columns[df.isnull().any()]

# Print the results
print("Dataset contains null values:", has_null_values)
print("Columns with null values:", columns_with_nulls.tolist()) 
```

**Exercise 06: Remove the null values (NAs) from the dataset, if applicable**
```python
# Original DataFrame size
original_size = df.shape

# Remove rows with any null values
df_cleaned = df.dropna() 

# New DataFrame size
cleaned_size = df_cleaned.shape

# Compare sizes
print("Original DataFrame size:", original_size)
print("Cleaned DataFrame size:", cleaned_size)
print("Number of rows removed:", original_size[0] - cleaned_size[0]) 
```

**Exercise 07: What is the average price in the population of "Arroyomolinos (Madrid)"?**
```python
# Filter the DataFrame for the specified population
arroyomolinos_df = df[df['level5'] == 'Arroyomolinos (Madrid)'] 

# Calculate the average price
average_price_arroyomolinos = arroyomolinos_df['price'].mean()

# Print the average price
print("Average price in Arroyomolinos (Madrid):", average_price_arroyomolinos) 
```


**Exercise 08: Plot the histogram of prices for the population of "Arroyomolinos (Madrid)" and explain what you observe**
```python
import matplotlib.pyplot as plt

# Create a histogram of prices for Arroyomolinos (Madrid)
plt.hist(arroyomolinos_df['price'], bins=20) 
plt.xlabel("Price")
plt.ylabel("Frequency")
plt.title("Histogram of Prices in Arroyomolinos (Madrid)")
plt.show() 

# Brief analysis of the plot
print("The histogram shows the distribution of house prices in Arroyomolinos (Madrid). \n" 
      "It appears to be right-skewed, indicating that there are more houses with lower prices and fewer houses with very high prices.")  
```