import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("StudentsPerformance.csv")

print("Dataset Shape:", df.shape)
print("\nDataset Info:")
print(df.info())
print("\nStatistical Summary:")
print(df.describe())

print("\nMissing Values:\n", df.isnull().sum())

print("\nAverage Scores:")
print(df[['math score', 'reading score', 'writing score']].mean())

print("\nGender-wise Average Scores:")
print(df.groupby('gender')[['math score', 'reading score', 'writing score']].mean())

df[['math score', 'reading score', 'writing score']].hist(figsize=(9,5))
plt.suptitle("Score Distribution")
plt.show()

sns.boxplot(x='gender', y='math score', data=df)
plt.title("Gender vs Math Score")
plt.show()

sns.heatmap(df[['math score','reading score','writing score']].corr(),
            annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap")
plt.show()
