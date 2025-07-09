# SAWA-5
# Dynamic Pricing for Urban Parking Lots

## Overview
This repository contains the code and documentation for a capstone project developed for Summer Analytics 2025, hosted by the Consulting & Analytics Club in collaboration with Pathway. The project implements a dynamic pricing system for 14 urban parking lots, optimizing utilization based on real-time demand, traffic conditions, and competitor prices. The solution is built in Google Colab and deployed on GitHub for submission.

## Tech Stack
- **Python**: Core programming language.
- **Pandas & NumPy**: Data manipulation and numerical computations.
- **Pathway**: Real-time data processing and streaming.
- **Bokeh & Panel**: Interactive data visualization and dashboarding.
- **Google Colab**: Development and execution environment.

## Architecture Flow
1. **Data Ingestion**:
   - Load `dataset.csv` containing parking lot data (e.g., `Occupancy`, `Capacity`, `TrafficConditionNearby`).
   - Preprocess data to create `parking_stream.csv` and `nearby_pairs.csv` for streaming.
2. **Real-Time Processing**:
   - Use Pathway to define schemas (`Parking`, `Nearby`) and compute three pricing models.
   - Model 1: Linear pricing based on occupancy.
   - Model 2: Adjusts for traffic, queue length, and special days.
   - Model 3: Incorporates competitor prices within 1 km.
3. **Visualization**:
   - Render interactive Bokeh plots with Panel tabs for each model.
   - Add scatter points, custom date ticks, and hover tools.
4. **Output**:
   - Generate Pandas DataFrames for analysis and serve visualizations in Colab.

### Architecture Diagram

[Data Source: dataset.csv] --> [Preprocessor: Pandas] --> [Pathway Pipeline]
|                              |                     |
v                              v                     v
[parking_stream.csv]    [nearby_pairs.csv]    [Model 1, 2, 3 Computations]
|                              |                     |
v                              v                     v
[Pathway Stream]    [Pathway Stream]    [Bokeh/Panel Visualization]
\                              /                     |
\                            /                      v
\                          /               [Interactive Dashboard]
\                        /
[Join for Model 3] --> [Output DataFrames]
