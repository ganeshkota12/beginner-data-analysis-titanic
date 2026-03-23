# 📊 Titanic Survival Analysis

## 🚀 Overview

This project analyzes the Titanic dataset to understand survival patterns using data preprocessing and exploratory data analysis (EDA).

---

## 📁 Dataset

* Titanic Dataset (CSV file)
* Features used:

  * PassengerId
  * Pclass
  * Name
  * Sex
  * Age
  * SibSp
  * Parch
  * Fare
  * Embarked
  * Survived

---

## ⚙️ Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google Colab / Jupyter Notebook

---

## 🧹 Data Preprocessing

### Load Dataset

```python
import pandas as pd

df = pd.read_csv('Titanic-Dataset (1).csv')
```

---

### Basic Data Inspection

```python
df.head()
df.info()
df.describe()
```

---

### Handle Missing Values (Age)

```python
df['Age'] = df['Age'].fillna(df['Age'].mean())
```

---

### Remove Unnecessary Column

```python
df.drop('Embarked', axis=1, inplace=True)
```

---

### Feature Engineering (Age Groups)

```python
df['Age_Group'] = pd.cut(df['Age'], bins=[0, 18, 35, 60, 100])
```

---

## 📊 Exploratory Data Analysis

### Survival Counts

```python
df['Survived'].value_counts()
```

---

### Average Survival Rate (Overall)

```python
df['Survived'].mean()
```

---

### Survival Rate by Gender

```python
df.groupby('Sex')['Survived'].mean()
```

---

### Survival Rate by Passenger Class

```python
df.groupby('Pclass')['Survived'].mean()
```

---

### Survival Rate by Age Group

```python
df.groupby('Age_Group', observed=True)['Survived'].mean()
```

---

### Mean Age

```python
df['Age'].mean()
```

---

## 📈 Data Visualization

### Survival Count Plot

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(x='Survived', data=df)
plt.title('Survival Count')
plt.show()
```

---

### Survival by Gender

```python
sns.countplot(x='Sex', hue='Survived', data=df)
plt.title('Survival by Gender')
plt.show()
```

---

### Survival by Passenger Class

```python
sns.countplot(x='Pclass', hue='Survived', data=df)
plt.title('Survival by Passenger Class')
plt.show()
```



### Survival by Age Group (Bar Plot)

```python
df.groupby('Age_Group', observed=True)['Survived'].mean().plot(kind='bar')
plt.title('Survival Rate by Age Group')
plt.ylabel('Survival Rate')
plt.show()
```

---

## 🧠 Conclusion

* Survival count shows more passengers did not survive
* Female passengers had higher survival rates than males
* First-class passengers had better survival chances
* Age groups show variation in survival probability
* Mean age was used to handle missing values

---
