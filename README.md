# smart-energy-meter-monitoring-system-
CREATE TABLE EnergyMeterData (
    id INT PRIMARY KEY AUTO_INCREMENT,
    meter_id VARCHAR(50),
    voltage FLOAT,
    current FLOAT,
    power FLOAT,
    energy_consumed FLOAT,
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
