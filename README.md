# Smart Farm Dashboard

This project implements a real-time dashboard for monitoring synthetic sensor data from a smart farm. It generates data at regular intervals, stores it in InfluxDB, and streams it to a React front-end using FastAPI.

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Endpoints](#endpoints)
- [Data Generation](#data-generation)
- [Contributing](#contributing)

## Features

- Real-time monitoring of synthetic sensor data (temperature, humidity, soil moisture).
- Data storage in a time-series database (InfluxDB).
- FastAPI backend for data ingestion and streaming.
- React front-end for data visualization using charts.
- Easy to extend for additional features and sensors.

## Architecture

1. **Data Generation**: A Python script generates synthetic sensor data every 30 seconds.
2. **Data Storage**: The generated data is stored in InfluxDB.
3. **Backend API**: FastAPI handles data ingestion and provides endpoints for data retrieval and streaming.
4. **Frontend**: A React application visualizes the data in real time.

## Requirements

- Python 3.8+
- FastAPI
- InfluxDB
- React (create-react-app)
- Requests library for Python
- InfluxDB Python client

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/smart-farm-dashboard.git
   cd smart-farm-dashboard
   ```

2. **Set up the Python environment**:
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   pip install fastapi[all] influxdb requests
   ```

3. **Set up InfluxDB**:
   - Install InfluxDB and start the service. 
   - Create a database named `sensor_data`:
     ```bash
     influx
     CREATE DATABASE sensor_data
     ```

4. **Set up the React frontend**:
   ```bash
   cd ../frontend
   npx create-react-app .
   npm install chart.js react-chartjs-2
   ```

## Usage

1. **Start the FastAPI server**:
   ```bash
   cd backend
   uvicorn main:app --reload
   ```

2. **Run the data generation script**:
   ```bash
   python data_generator.py
   ```

3. **Start the React app**:
   ```bash
   cd frontend
   npm start
   ```

4. **Open the dashboard**:
   - Navigate to `http://localhost:3000` in your web browser.

## Endpoints

- **POST /api/sensor-data**: Receives sensor data and stores it in InfluxDB.
  - **Request Body**:
    ```json
    {
      "time": "2024-09-27T12:00:00Z",
      "temperature": 25.0,
      "humidity": 60.0,
      "soil_moisture": 0.75
    }
    ```

- **GET /api/historical-data**: Retrieves historical sensor data from InfluxDB.

## Data Generation

The data generation script runs in the background and simulates sensor readings every 30 seconds. The values are randomly generated within realistic ranges for temperature, humidity, and soil moisture.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue.
