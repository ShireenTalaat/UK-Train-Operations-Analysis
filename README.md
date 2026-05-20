# 🚆 UK Train Ride Analysis – Operational, Sales, Weather & Passenger Insights

### 📊 Power BI Project by Shireen Talaat

This Power BI report presents an extensive end-to-end analysis of **UK train operations**, focusing on **operational efficiency**, **sales performance**, **weather impact**, and **passenger behavior**.  
The dataset was cleaned, modeled, and analyzed to extract actionable insights that can help improve service reliability, revenue, and passenger satisfaction.

---

## 🧭 Project Overview

The analysis aims to answer four main business questions:

1. **Operational Analysis:**  
   How efficiently are train services operating across different routes, times, and stations?

2. **Sales Performance:**  
   Which ticket types and routes drive the highest revenue, and what patterns exist in sales trends?

3. **Weather Impact:**  
   How do weather conditions affect train delays, cancellations, and overall operational costs?

4. **Passenger Behavior:**  
   How do passengers respond to delays, cancellations, and varying weather conditions?

---

## 🗂️ Data Model & Structure

The Power BI data model integrates several related tables:

- **Railway Table:** Train journey details (departure, arrival, delay duration, status, reason for delay, etc.)  
- **Weather Tables:** Separate data for **departure** and **arrival** weather, including temperature, rainfall, wind speed, and condition codes.  
- **JourneyWithWeather Table:**  
  A filtered table containing only **delayed or cancelled journeys due to weather conditions**, used for deep analysis.

Key relationships:
- `Railway` ↔ `DepartureWeather`  
- `Railway` ↔ `ArrivalWeather`
- `Railway` ↔ `BankHolidays`

---

## ⚙️ Data Preparation Steps

1. **Data Cleaning** – Removed nulls, standardized columns, ensured consistent datetime formats.  
2. **Filtering:** Created a calculated table `JourneyWithWeather` with:
   ```DAX
   JourneyWithWeather = 
   FILTER(
       Railway,
       Railway[Journey Status] IN {"Delayed", "Cancelled"} 
       && Railway[Reason for Delay] = "Weather"
   )
