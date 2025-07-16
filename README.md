# chatbot
pip install pandas scikit-learn matplotlib
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

# Load dataset
url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv"
columns = ["Pregnancies", "Glucose", "BloodPressure", "SkinThickness", "Insulin",
           "BMI", "DiabetesPedigreeFunction", "Age", "Outcome"]
df = pd.read_csv(url, names=columns)

# Features and target
X = df.drop("Outcome", axis=1)
y = df["Outcome"]

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Scale the data
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Train model
model = LogisticRegression()
model.fit(X_train_scaled, y_train)

# Get user input
print("Enter the following health details to predict diabetes:")

try:
    user_data = [
        float(input("Pregnancies: ")),
        float(input("Glucose: ")),
        float(input("BloodPressure: ")),
        float(input("SkinThickness: ")),
        float(input("Insulin: ")),
        float(input("BMI: ")),
        float(input("DiabetesPedigreeFunction: ")),
        float(input("Age: "))
    ]

    # Scale user input
    user_data_scaled = scaler.transform([user_data])

    # Make prediction
    prediction = model.predict(user_data_scaled)[0]

    # Output result
    if prediction == 1:
        print("\n🔴 The person is likely to be **Diabetic**.")
    else:
        print("\n🟢 The person is likely to be **Non-Diabetic**.")

except ValueError:
    print("❌ Invalid input! Please enter numeric values.")


