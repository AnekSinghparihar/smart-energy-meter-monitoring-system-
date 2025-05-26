# ⚡ Smart Energy Monitoring System (SQL Project)

A simple and efficient SQL-based project that monitors and analyzes electricity usage from multiple energy meters. Perfect for learning database design, analytics, and integration with IoT or backend systems.

---

## 📌 Project Overview

This project simulates a **Smart Energy Monitoring System** using SQL. It stores energy usage data (voltage, current, power, energy consumed) from different meters and provides insights through queries such as:

- Total energy consumed
- Daily consumption reports
- Peak power usage

---

## 🛠️ Technologies Used

- **SQL (Structured Query Language)**
- Compatible with:
  - SQLite ✅
  - MySQL ✅
  - PostgreSQL ✅
- Online SQL Compilers (e.g. [DB-Fiddle](https://www.db-fiddle.com/), [SQL Fiddle](http://sqlfiddle.com/))
- Optional GUI Tools: DBeaver, SQLiteStudio, phpMyAdmin

---

## 🧱 Database Schema

```sql
CREATE TABLE EnergyMeterData (
    id INTEGER PRIMARY KEY,  -- For MySQL: use AUTO_INCREMENT
    meter_id TEXT,
    voltage REAL,
    current REAL,
    power REAL,
    energy_consumed REAL,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
INSERT INTO EnergyMeterData (meter_id, voltage, current, power, energy_consumed)
VALUES 
('MTR001', 230.0, 5.2, 1196.0, 0.5),
('MTR001', 231.0, 4.8, 1108.8, 0.45),
('MTR002', 228.0, 6.0, 1368.0, 0.55),
('MTR001', 229.5, 5.0, 1147.5, 0.49),
('MTR002', 230.0, 5.5, 1265.0, 0.52);
SELECT meter_id, SUM(energy_consumed) AS total_energy
FROM EnergyMeterData
GROUP BY meter_id;
SELECT DATE(timestamp) AS date, meter_id, SUM(energy_consumed) AS daily_energy
FROM EnergyMeterData
GROUP BY DATE(timestamp), meter_id;
SELECT meter_id, MAX(power) AS peak_power
FROM EnergyMeterData
GROUP BY meter_id;


📦 smart-energy-monitoring-sql
├── README.md              # Project documentation
├── schema.sql             # SQL schema definition
├── insert_data.sql        # Sample meter data
└── queries.sql            # SQL queries for analysis
