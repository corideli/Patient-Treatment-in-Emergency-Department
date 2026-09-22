# Patient Treatment in Emergency Department

Business Information Systems Project
Academic Year 2025–2026

## Project Overview

This project analyses patient stays in an Emergency Department using Process Mining techniques.

The objective is to study the recorded patient flow, measure Length of Stay (LOS), identify repeated activities and process variants, and compare different process discovery models.

The analysis was developed in Google Colab using Python, pandas and PM4Py.

## Dataset

The original event log contains:

* 25,115 rows
* 1,820 recorded stays
* 16,826 process events after data preparation
* 896 different process variants

Each case is identified by `stay_id`.

The original dataset is confidential and is therefore **not included in this repository**.

## Analysis

The notebook includes the following steps:

### Data Preparation

The dataset is checked for missing values, duplicates and repeated combinations of stay, timestamp and activity.

A process table is created with one event for each unique combination of:

`stay_id + timestamp + activity`

### Variant Analysis

The different sequences of activities followed by patients are analysed to understand the variability of the process.

### Length of Stay

Length of Stay is calculated from **Enter the ED** to **Discharge from the ED**.

The median recorded LOS is approximately 301 minutes.

### Group Comparison

Length of stay is compared across:

* Acuity levels
* Arrival modes
* Disposition groups

### Directly-Follows Graphs

Frequency and performance Directly-Follows Graphs are generated to analyse activity connections and the time between consecutive events.

### Process Discovery

Different process models are created using:

* Inductive Miner
* Heuristics Miner
* Inductive Miner on subsets of the most frequent variants

The models are evaluated on the complete log using Fitness, Precision and F1 score.

The selected model is **Inductive top6**, with approximately:

* Fitness: 0.863
* Precision: 0.986
* F1 score: 0.921

### Conformance Checking

Token-based replay is used to compare the recorded patient paths with the selected Petri Net.

### Binary Pattern Analysis

Patient stays are also grouped according to acuity and arrival mode to compare their recorded Length of Stay.

## Main Results

The analysis shows a highly variable process with many different recorded paths.

Some patient groups, especially transferred patients, have considerably longer stays.

Repeated activities and long inter-event intervals identify areas that could be investigated further, although the available data alone cannot establish their causes.

## Proposed Improvements

Three possible areas for further investigation are identified:

1. Improve event identifiers and timestamp quality.
2. Investigate repeated clinical activities together with clinical staff.
3. Analyse long transfer stays in greater detail.

## Repository Contents

`BIS_exam.ipynb` – Complete Google Colab notebook containing the Process Mining analysis.

`README.md` – Description of the project and repository.

## Technologies

* Python
* Google Colab
* pandas
* NumPy
* Matplotlib
* PM4Py 2.7.23.8

## Running the Notebook

The notebook can be opened in Google Colab.

The original dataset is not distributed with this repository because it is confidential.

To reproduce the analysis, the file `dataset_for_exam.csv` must be made available to the notebook through Google Drive or uploaded manually when requested.

## Author

Corinne D'Elia
Business Information Systems
Academic Year 2025–2026
