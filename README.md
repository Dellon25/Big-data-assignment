# 🚕 Uber Rides Data Analysis & Visualization

**Student**: Manzi Delphin  
**ID**: 26021  
**Lecturer**: Maniraguha Eric  
**Course**: Big Data 
**Assignment**: Uber Ride Dataset – Full Analysis & Power BI Dashboard

---

## 📁 Project Overview

This project analyzes Uber ride data using Python for data preparation and Power BI for building a comprehensive interactive dashboard. It covers time trends, fare distributions, and geospatial patterns of rides. The entire workflow includes data cleaning, feature engineering, visualization, and documentation.

---

## 📦 Submission Requirements

### ✅ Deliverables

1. **Power BI Dashboard File (`UberDashboard.pbix`)**
   - Interactive visualizations
   - Fare analysis by time, day, and location
   - Professionally formatted and user-friendly dashboard

2. **GitHub Repository**
   - `enhanced_uber_dataset.csv`: Cleaned dataset
   - `/screenshots/`: Documentation images (loading, cleaning, dashboard)
   - `README.md`: Project explanation and structure

3. **Documentation Screenshots**
   - 📥 **Data Loading Process**  
     <img width="877" height="820" alt="data loading  process" src="https://github.com/user-attachments/assets/5d34f2f2-34c4-4512-8e91-66f8a3f4dc6f" />

   - 🧹 **Data Cleaning Steps and Output**  
     <img width="995" height="841" alt="data cleaning steps " src="https://github.com/user-attachments/assets/8a49081d-11f5-4e60-9e21-28a216dcc44f" />
     <img width="601" height="636" alt="data cleaning steps  output" src="https://github.com/user-attachments/assets/186d5f08-472c-4ebe-bb70-fdd0f9d10aad" />


   - 💾 **Export Cleaned Dataset to CSV**  
    <img width="1077" height="258" alt="export cleaned  dataset" src="https://github.com/user-attachments/assets/434b5147-9e4e-4853-83b0-5ca0ef1e9938" />

   - 📊 **Dashboard Development (Power BI)**  
    <img width="1140" height="611" alt="dashboard" src="https://github.com/user-attachments/assets/6717f495-1d84-4393-ae1a-14455df7ebbe" />

    

4. **Final Report Format**
   - ✅ Option A: Markdown report (this file) in GitHub repository

---

## 🧪 Data Cleaning & Feature Engineering

Performed using Python (pandas, numpy):

```python
# Load and clean dataset
df = pd.read_csv("uber.csv")
df['pickup_datetime'] = pd.to_datetime(df['pickup_datetime'], errors='coerce')
df.dropna(inplace=True)

# Feature Engineering
df['hour'] = df['pickup_datetime'].dt.hour
df['day'] = df['pickup_datetime'].dt.day
df['month'] = df['pickup_datetime'].dt.month
df['day_of_week'] = df['pickup_datetime'].dt.dayofweek
df['is_peak'] = df['hour'].apply(lambda x: 1 if (7 <= x <= 9 or 16 <= x <= 19) else 0)
df['day_type_encoded'] = df['day_of_week'].apply(lambda x: 1 if x >= 5 else 0)

# Save cleaned dataset
df.to_csv("enhanced_uber_dataset.csv", index=False)
