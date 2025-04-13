# 📊 Systematic Sampling in Python  
**Using the Iris Dataset**

This repository contains a practical example of **systematic sampling** implemented in Python using the classic [Iris dataset](https://archive.ics.uci.edu/ml/datasets/iris). The example is structured in a Jupyter Notebook and demonstrates how to draw a sample from a dataset using a fixed interval method.

---

## 📌 What is Systematic Sampling?

Systematic sampling is a sampling method where elements are selected from an ordered population at regular intervals. For example, to extract a sample of 15 elements from a population of 150, you randomly pick a starting point and then select every 10th element.

---

## 🧠 Step-by-Step Explanation

### 1. 📥 Importing Libraries

```python
import pandas as pd
import numpy as np
from math import ceil
```

---

### 2. 📏 Define Population, Sample Size, and Interval

```python
population = 150
sample = 15
k = ceil(population / sample)
print(k)  # Output: 10
```

- `population`: Total number of elements.
- `sample`: Desired number of sample elements.
- `k`: Sampling interval (`ceil(population/sample)`).

---

### 3. 🎯 Random Starting Point

```python
r = np.random.randint(low=1, high=k + 1, size=1)
print(r)  # Example: [8]
```

- Randomly selects a starting index between 1 and `k`.

---

### 4. 🔁 Generate Sample Indexes

```python
cumulative = r[0]
raffle = []
for i in range(sample):
    raffle.append(cumulative)
    cumulative += k

print(raffle)
# Output: [8, 18, 28, ..., 148]
```

- Iteratively builds a list of indexes by adding `k` each time.

---

### 5. 📄 Load Dataset and Select Sample

```python
dataset = pd.read_csv('iris.csv')
dataset_final = dataset.loc[raffle]
dataset_final
```

- Loads the Iris dataset from a CSV file.
- Filters it using the previously generated sample indexes.

---
