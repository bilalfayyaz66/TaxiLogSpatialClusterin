TaxiLogSpatialClustering
This repository contains the implementation the project that analyzes taxi GPS log data from February 2–8, 2008, to identify spatial clusters using the DBSCAN algorithm. The analysis includes data preprocessing, visualization, spatial hashing, candidate pair generation, and clustering evaluation.
Table of Contents

Project Overview
Dataset
Requirements
Installation
Analysis Steps
Results
License

Project Overview
The goal of this project is to process taxi GPS log data to identify clusters of taxi locations, representing areas of high activity (e.g., taxi hotspots). The analysis employs spatial hashing to optimize data organization and uses the DBSCAN clustering algorithm to group points based on geographic proximity.
 Key tasks include:

Loading and preprocessing taxi log data.
Visualizing spatial and temporal patterns.
Implementing spatial hashing and banding for efficient clustering.
Generating candidate pairs for clustering.
Applying DBSCAN and evaluating clustering quality.

Dataset
The dataset consists of taxi GPS logs stored in multiple .txt files. 
Each file contains:

ID: Taxi identifier (integer)
Timestamp: Date and time of the GPS record (YYYY-MM-DD HH:MM:SS)
Longitude: Longitude coordinate (float)
Latitude: Latitude coordinate (float)

The analysis processes the first 40 files, resulting in a DataFrame with 63,593 records from February 2–8, 2008.
Dataset Download link: https://1drv.ms/u/s!AsWQUIUFkRXPgsN6OCa9OB-qziGfhA

Download the dataset from the provided link.
Place the .txt files in a data/taxi_log_2008_by_id directory in the repository root.
Ensure the files are comma-separated and follow the format: ID,Timestamp,Longitude,Latitude.

Requirements

Python 3.11
Libraries:
pandas
matplotlib
seaborn
numpy
scikit-learn
geopy



Installation

Clone the Repository:Clone the repository to your local machine and navigate to the project directory:
git clone https://github.com/bilalfayyaz66/TaxiLogSpatialClustering.git
cd TaxiLogSpatialClustering


Set Up a Virtual Environment (recommended):Create and activate a Python virtual environment to isolate dependencies:
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Set Up the Dataset:

Download the dataset from the provided link.
Create a data/taxi_log_2008_by_id directory in the repository root and place the .txt files there.
The notebook uses a relative path (data/taxi_log_2008_by_id). If your dataset is located elsewhere, update the path to match your dataset location.


Run the cells in sequence to:
Load and preprocess the taxi log data.
Visualize data with time series plots, scatter plots, and histograms.
Perform spatial hashing and banding.
Generate candidate pairs for clustering.
Apply DBSCAN clustering and evaluate results.


View the output, including cluster visualizations and performance metrics (e.g., silhouette score).

Analysis Steps

Data Loading and Preparation:
Loaded 40 .txt files into a Pandas DataFrame.
Converted columns: ID to integer, Timestamp to datetime, Longitude and Latitude to float.


Data Exploration and Visualization:
Displayed the first 15,000 rows.
Created time series plots (longitude/latitude vs. time), scatter plots (longitude vs. latitude), and histograms.


Spatial Hashing and Banding:
Implemented hash_to_grid to convert coordinates to grid cells.
Used divide_into_bands to group hashed coordinates into spatial bands.


Candidate Pair Generation:
Identified pairs of nearby points within each band for efficient clustering.


Distance Calculation and Clustering:
Used the haversine_distance function to compute great-circle distances.
Appliy DBSCAN clustering (eps=0.5, min_samples=5) to the full dataset and candidate pairs.
Evaluated clusters using the silhouette score.

Performance Evaluation:
Measure DBSCAN execution time and clustering quality.

Results

Dataset Size: 63,593 GPS records.
Execution Time: 0.33 seconds for DBSCAN on the full dataset.
Silhouette Score: 0.883, indicating high-quality, well-separated clusters.
Visualizations: Scatter plots showed distinct clusters of taxi locations, color-coded by DBSCAN labels.


License
This project is licensed under the MIT License. See the LICENSE file for details.

