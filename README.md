
import pandas as pd
import matplotlib.pyplot as plt

# Create sample logistics data
data = {
    "Order_ID": [101, 102, 103, 104, 105, 106],
    "Delivery_Time": [2, 4, 3, 6, 5, 2],
    "Expected_Time": [3, 3, 4, 4, 5, 3],
    "Delivery_Cost": [100, 150, 120, 200, 180, 90]
}

df = pd.DataFrame(data)

# Display the dataset
print("Logistics Delivery Data:")
print(df)

# Calculate KPIs
on_time = (df["Delivery_Time"] <= df["Expected_Time"]).mean() * 100
avg_time = df["Delivery_Time"].mean()
avg_cost = df["Delivery_Cost"].mean()

print("\nKey Performance Indicators (KPIs)")
print("On-Time Delivery Rate:", round(on_time, 2), "%")
print("Average Delivery Time:", round(avg_time, 2))
print("Average Delivery Cost:", round(avg_cost, 2))

# Check missing values and duplicates
print("\nMissing Values:")
print(df.isnull().sum())

print("\nDuplicate Rows:", df.duplicated().sum())

# Visualize delivery time
plt.bar(df["Order_ID"].astype(str), df["Delivery_Time"])
plt.xlabel("Order ID")
plt.ylabel("Delivery Time (hours)")
plt.title("Logistics Delivery Time Analysis")
plt.tight_layout()
plt.show()

# Identify delayed orders
delayed = df[df["Delivery_Time"] > df["Expected_Time"]]
print("\nDelayed Orders:")
print(delayed)

# Conclusion
print("\nAnalysis completed successfully!")
