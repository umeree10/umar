import pandas as pd
from sklearn.preprocessing import MinMaxScaler, LabelEncoder

# Load the dataset
df = pd.read_csv("train.csv")

# Drop the 'id' column
df = df.drop('id', axis=1)

# Encode the 'Sex' column
le = LabelEncoder()
df['Sex'] = le.fit_transform(df['Sex'])  # male=1, female=0 (assuming same mapping)

# Scale numeric features using Min-Max Scaler
scaler = MinMaxScaler()
numeric_features = ['Age', 'Height', 'Weight', 'Duration', 'Heart_Rate', 'Body_Temp', 'Calories']
df[numeric_features] = scaler.fit_transform(df[numeric_features])

# Show the first few rows of the preprocessed data
print(df.head(3))  # printing 3 rows instead of default 5
