# 🛠️ Google Forms Data Analysis Using Power BI

## 📖 Introduction  
This project demonstrates the transformation of raw data collected via Google Forms in Excel format into an interactive dashboard using **Power BI**. The goal was to clean, structure, and analyze the data to extract actionable KPIs, providing clear insights for decision-making.  

---

## 🚀 Project Overview  
### Objectives:  
- Extract key performance indicators (KPIs) as per the client's requirements.  
- Address data inconsistencies and prepare it for analysis.  
- Develop a user-friendly, interactive Power BI dashboard.  

### Key Challenges:  
1. **Data Organization**:  
   - The raw data contained multiple details (country, governorate, city) combined in one column with inconsistent formatting.  
   - Missing Data Validation led to repetitive and inaccurate entries.  

2. **Strict Deadline**:  
   - The project had to be completed within 3 days.  

### Solutions:  
- **Data Cleaning**:  
   - Used **Python** to split the combined location column into three distinct columns (country, governorate, city).  
   - Unified values using manual replacements to ensure consistency.  
   - Standardized text formatting (removed extra spaces, corrected case sensitivity).  

- **Dashboard Development**:  
   - Created an interactive Power BI dashboard to visualize KPIs and additional insights.  
   - Focused on storytelling to make the dashboard user-friendly and insightful.

---

## 🧰 Tools & Technologies  
- **Excel**: For initial data review and cleanup.  
- **Python**: For advanced data cleaning and column restructuring.  
- **Power BI**: To design the dashboard and deliver insights.  

---

## 📊 Dashboard Features  
- **Geographical Analysis**: Breakdown of data by country, governorate, and city.
  
<img width="676" alt="image" src="https://github.com/user-attachments/assets/98e12a9d-e0db-4918-a9cf-874fd0a4581b">

- **Participant Insights**: Key metrics like distribution, preferences, and behaviors.

<img width="700" alt="image" src="https://github.com/user-attachments/assets/f1fadd73-0cfa-4446-983a-6f3ec2f07586">

- **Custom KPIs**: Additional indicators proposed to enhance client decision-making.

<img width="807" alt="image" src="https://github.com/user-attachments/assets/ab9fbfc2-872f-4011-bc13-1bc0164f01af">

---

## 📝 Key Takeaways  
- Cleaning and organizing raw data is the foundation for meaningful analysis.  
- Leveraging Python and Power BI together ensures efficiency and clarity in presenting data.  
- Storytelling with data helps communicate complex information effectively.

---

## 🔑 Python Code for Data Cleaning  

```python
# Rename column for easier handling
df.rename(columns={'البلد و المحافظة السكنية و المدينة / مثال : ( مصر - القاهرة - مدينة نصر )': 'Location'}, inplace=True)

# Function to split the location into country, governorate, and city
def split_location(location):
    if isinstance(location, str):
        parts = [part.strip() for part in location.replace('-', ' ').replace('_', ' ').split()]
        country = parts[0] if len(parts) > 0 else None
        governorate = parts[1] if len(parts) > 1 else None
        place = parts[2] if len(parts) > 2 else None
        return pd.Series([country, governorate, place])
    else:
        return pd.Series([None, None, None])

# Apply the function to the location column
df[['Country', 'Governorate', 'City']] = df['Location'].apply(split_location)

# Clean and standardize text formatting
df['Location'] = df['Location'].str.replace('-', ' ').str.strip().str.title()
df['Location'] = df['Location'].str.replace('_', ' ').str.strip().str.title()

# Replace inconsistent values manually
df2['Governorate'] = df2['Governorate'].replace({
    'الجيزه': 'الجيزة',
    'القاهره': 'القاهرة',
    '_القاهرة': 'القاهرة',
    'Cairo': 'القاهرة',
    'Egypt': 'القاهرة',
    'Giza': 'الجيزة',
    'Alex': 'الاسكندرية',
    'الاسكندريه': 'الاسكندرية'
})
```

---


## 🖼️ Dashboard Preview
Check out the interactive dashboard in action!  
[Interactive Dashboard Video](https://www.linkedin.com/posts/mohamedalqmash_storytelling-python-datacleaning-activity-7271896531954245632-_r8z?utm_source=share&utm_medium=member_desktop)

**Description**:  
This video demonstrates how the Power BI dashboard provides interactive visualizations of key performance indicators (KPIs), allowing users to explore the data based on geographic locations, participant insights, and more. The dashboard is designed for easy navigation and provides actionable insights for decision-making.

## 🔚 Conclusion  
This project showcases the power of combining data cleaning techniques with advanced visualization tools like Power BI to transform raw data into valuable insights. By addressing challenges such as data inconsistency and tight deadlines, the project demonstrates how effective data analysis can lead to informed decision-making and improved business outcomes.  

Feel free to explore the code, dashboard, and share any feedback or questions you may have!  
Together, we can continue improving how we work with data and turn it into impactful stories.

---
