# INDENG-290-Project-Fire-Department-Surge-Dispatch-Simulation
Tianze Liu, Yun Zhang, and Jiarui Wen

## Overview
This repository implements a discrete‐event simulation of San Francisco Fire Department dispatch operations under both normal and surge conditions. It demonstrates how priority‐based queuing and cross‐district resource sharing can dramatically improve response to high-demand events.

## Features
- Priority Queueing: Calls are ranked by urgency and waiting time.
- Surge Mode: When a district’s pending calls exceed a threshold, spare engines across all stations are redeployed for global optimization.
- Global vs. Local Dispatch:
- Normal: Greedy, nearest-neighbor assignment across all districts.
- Surge: Hungarian‐method assignment over all pending calls and available units.
- Max-Wait Enforcement: Calls expire as “failed” if waiting time exceeds a type-specific limit.

# Metrics & Visualization:
- Dispatch success/failure rates by priority and mode
- Response time and handling‐time summaries
- Backlog curves illustrating surge clearing

# Getting Started
## Prerequisites
- Python 3.8+
- pandas, numpy, geopy, scipy, matplotlib

## Running the Simulation
- Load station data (SF_Facilities.csv)
- Generate or load calls (simulated_calls.csv / surge_simulated_calls.csv)
- Configure parameters at the top of the notebook:EMERGENCY_SPEED, alpha, beta, DISTRICT_SURGE_TRIGGER, DISTRICT_SURGE_EXIT, service_time_mapping, priority_mapping, max_wait_mapping
- Execute the main loop cell to simulate dispatch and record dispatch_records.
- Run metrics cells to produce summary tables and plots.

# Outputs & Visualizations
- Overall dispatch success rates
- Priority-level solve/fail percentages
- Response time & total handling time comparisons
- Backlog‐clearing curves for surged districts
- Boxplots of response‐time distributions

# Interpretation
- Normal mode (greedy) suffices for day-to-day operations—100 % success under realistic call volumes.
- Surge mode is critical to handle extreme spikes (e.g., earthquakes), boosting priority‐1 solve rates from ~42 % to ~70 % and clearing backlogs an order of magnitude faster.
