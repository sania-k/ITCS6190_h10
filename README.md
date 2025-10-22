# Handson-L10-Spark-Streaming-MachineLearning-MLlib
---
## **Overview**

A real-time analytics pipeline for a ride-sharing platform using Apache Spark strucutred Streaming and MLlib. Includes processing streaming data, implementing machine learning algorithms, and predicting various features.

---

## **Prerequisites**
Before running, ensure you have the following software installed and properly configured on your machine:
1. **Python 3.x**:
   - [Download and Install Python](https://www.python.org/downloads/)
   - Verify installation:
     ```bash
     python3 --version
     ```

2. **PySpark**:
   - Install using `pip`:
     ```bash
     pip install pyspark
     ```
3. **Numpy**:
   - Install using `pip`:
     ```bash
     pip install numpy
     ```

---
## **Project Structure**
```
├── models/
│   ├── fare_model
│   |    └── data
│   |    └── metadata
|   ├── fare_trend_model_v2
│   |    └── data
│   |    └── metadata
├── task4.py
├── task5.py
├── data_generator.py
└── training-dataset.csv
```
- **data_generator.py/**: generates a constant stream of input data of the schema (trip_id, driver_id, distance_km, fare_amount, timestamp).
- **training-dataset.csv.py/**: contains training data for the linear regression modes. Tnput data contains five columns (trip_id, driver_id, distance_km, fare_amount, timestamp).
- **task_4**: Linear regession model learns relation between distance and fare amount. Live ride data is streamed from socket nad model is used to predict fare based on trip 
distance. Deviation between actual fare and predicted is calculated for anomalies. Model saves to `models/fare_model`.
- **task_5**: Training data is aggregated into 5-minute windows and average fare is calculated. Feature engineering is used to cycle through times of day 
and linear regression is used to train a model to preduct average fare at the times of day.g the avg_fare for each. Model saves to `models_fare_trend_model_v2`.
- **outputs/**: Model data and metadata from the tasks.
- **README.md**: Assignment instructions and guidelines. 

---

## **Running the Tasks**

You can run the analysis tasks either locally.

1. **Execute Each Task **: The data_generator.py should be continuosly running on a seperate terminal. Open a new terminal to execute each of the tasks.
   ```bash
     python data_generator.py
   ```
   ```bash
     python task4.py
   ```
   ```bash
     python task5.py
   ```

---

## **Output**
### Task 4 Output
Outputs a LinearRegressionModel to `models/fare_model` and streaming results to terminal in batches.
#### Example:
<img width="1747" height="847" alt="image" src="https://github.com/user-attachments/assets/44ed7911-2e52-41b4-b674-a6e14b4074a0" />

### Task 5 Output
Outputs a LinearRegressionModel to `models_fare_trend_model_v2` and streaming results to terminal in batches.
#### Example:
<img width="1179" height="243" alt="image" src="https://github.com/user-attachments/assets/e4adf8c3-096f-4bc0-b236-ff1931f6b0d2" />

## **Reflection**
In this assignment, I learnt the gist of how to use the machine learning library in pyspark. The assignment itself was straightforward, and I only ran into minor logic errors that came from initially fitting the model to the wrong data. 
