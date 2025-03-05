# Case-Vehicle-Population-Electric
## Preliminary Description
### The dataset called "Vehicle_popultaion_electric" consists of 223,496 instances, a set of 13 attributes, and one class, which describes different information about electric cars, their model, year of manufacture, types of them, among others. 

### How many data points does the dataset have? 
```bash
SELECT COUNT(*) 
FROM `vehicles_population.vehicles_population_data`
```
Results: 223.496 records

### What are the unique values in each column?
```bash
SELECT DISTINCT(County) 
FROM `vehicles_population.vehicles_population_data`
```
Results: 39 unique values

```bash
SELECT DISTINCT(City)
FROM `vehicles_population.vehicles_population_data`
```
Results: 484 unique values

```bash
SELECT DISTINCT(Make)
FROM `vehicles_population.vehicles_population_data`
```
Results: 46 unique values

```bash
SELECT DISTINCT(Model)
FROM `vehicles_population.vehicles_population_data`
```
Results: 164 unique values

```bash
SELECT DISTINCT(Model_Year)
FROM `vehicles_population.vehicles_population_data`
```
Results: 21 unique values

```bash
SELECT DISTINCT(Postal_Code)
FROM `vehicles_population.vehicles_population_data`
```
Results: 565 unique values

```bash
SELECT DISTINCT(Electric_Vehicle_Type)
FROM `vehicles_population.vehicles_population_data`
```
Results: 2 unique values

```bash
SELECT DISTINCT(Electric_Range)
FROM `vehicles_population.vehicles_population_data` 
```
Results: 109 unique values

```bash
SELECT DISTINCT(Base_MSRP)
FROM `vehicles_population.vehicles_population_data` 
```
Results: 31 unique values

```bash
SELECT DISTINCT(Legislative_District)
FROM `vehicles_population.vehicles_population_data`
```
Results: 49 unique values

```bash
SELECT DISTINCT(Electric_Utility)
FROM `vehicles_population.vehicles_population_data` 
```
Results: 75 unique values

```bash
SELECT DISTINCT(DOL_Vehicle_ID)
FROM `vehicles_population.vehicles_population_data` 
```
Results: 223496 unique values

```bash
SELECT DISTINCT(Clean_Alternative_Fuel_Vehicle__CAFV__Eligibility)
FROM `vehicles_population.vehicles_population_data`
```
Results: 3 unique values

### What is the oldest and most recent manufacturing year?
```bash
SELECT MAX(Model_Year), 
       MIN(Model_Year)
FROM `vehicles_population.vehicles_population_data`
```
Results: The oldest manufacturing is 1999 and the most recent manufacturing is 2025

### What is the city with more than 5,000 vehicle records?
```bash
SELECT City AS CITY, COUNT(*) AS QUAN 
FROM `vehicles_population.vehicles_population_data` 
GROUP BY CITY 
HAVING QUAN > 5000 
ORDER BY QUAN DESC 
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Max_registre%20by%20CITY.png?raw=true)

### How many records does each vehicle type have?
```bash
SELECT Electric_Vehicle_Type, COUNT(Electric_Vehicle_Type) AS Type_Registre_Veh
FROM `vehicles_population.vehicles_population_data` 
GROUP BY Electric_Vehicle_Type  
ORDER BY Type_Registre_Veh DESC 
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Type_Registre_Veh%20by%20Electric_Vehicle_Type.png?raw=true)

### What model and manufacturing year has the most records?
```bash
SELECT Model, Model_Year, COUNT(*) AS Vehicle_Registrate
FROM `vehicles_population.vehicles_population_data` 
GROUP BY Model, Model_Year 
ORDER BY Vehicle_Registrate DESC
LIMIT 1
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Model_Year,%20Vehicle_Registrate%20by%20Model.png?raw=true)

### What vehicle model has the most records in the city with the most records?
```bash
SELECT Model, COUNT(*) AS Max_Vehicle_Registrate
FROM `vehicles_population.vehicles_population_data` 
WHERE City = 'Seattle'
GROUP BY Model
ORDER BY Max_Vehicle_Registrate DESC
LIMIT 1
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Max_Vehicle_Registrate%20by%20Model.png?raw=true)

### What vehicle model has the highest and lowest mileage estimate?
```bash
SELECT Model, COUNT(*) AS Max_Range     
FROM `vehicles_population.vehicles_population_data` 
GROUP BY Model
ORDER BY Max_Range DESC
LIMIT 5
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Max_Range%20by%20Model.png?raw=true)

```bash
SELECT Model, COUNT(*) AS Min_Range     
FROM `vehicles_population.vehicles_population_data` 
GROUP BY Model
ORDER BY Min_Range ASC
LIMIT 5
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Min_Range%20by%20Model.png?raw=true)

### Will there be an increase or decrease in vehicle registrations based on their manufacturing year? 
```bash
SELECT Model_Year, COUNT(*) AS Diff_Vehicle_Registrate
FROM `vehicles_population.vehicles_population_data` 
GROUP BY Model_Year 
ORDER BY Model_Year DESC
```

![alt text](https://github.com/Barbara-Lizama/case-vehicle-population-electric/blob/master/Plots/Diff_Vehicle_Registrate%20by%20Model_Year.png?raw=true)