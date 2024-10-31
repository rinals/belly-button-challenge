# Belly Button Biodiversity Dashboard

## Overview

This project is an interactive dashboard built to explore the Belly Button Biodiversity dataset. The dataset catalogs various microbial species (referred to as Operational Taxonomic Units, or OTUs) found in human navels. The dashboard allows users to select different test subjects and view information about the microbial species present in each individual, as well as the demographic details of each test subject.

## Purpose

The purpose of this project is to:

1. Allow users to explore microbial biodiversity across individuals.
2. Visualize the top 10 bacterial species (OTUs) for each test subject.
3. Display demographic information associated with each test subject, such as ID, ethnicity, gender, age, location, and more.

## Features

- **Dropdown Menu**: A dynamic dropdown menu lets users select a test subject ID, automatically updating the dashboard with relevant data.
- **Demographic Information Panel**: Displays detailed demographic info for the selected test subject.
- **Bar Chart**: Shows the top 10 OTUs for the selected individual, ordered by sample value.
- **Bubble Chart**: Displays all OTUs for the selected individual, with the size of each bubble indicating sample value and color indicating OTU ID.

## Technical Summary

The project is built with:

- **HTML** for the structure.
- **JavaScript (D3.js)** for data handling and dynamic content updates.
- **Plotly.js** for creating interactive bar and bubble charts.
- **GitHub Pages** for hosting the static dashboard.

## Data Source

The Belly Button Biodiversity dataset is loaded from an external JSON file (`samples.json`). The data includes:

- `names`: An array of test subject IDs.
- `metadata`: An array of demographic information for each test subject.
- `samples`: An array of microbial sample data for each individual, including `otu_ids`, `sample_values`, and `otu_labels`.

## Project Files

- **index.html**: The main HTML file that includes the structure of the dashboard and references the necessary scripts.
- **app.js**: JavaScript file located in `static/js/` that handles data loading, processing, and chart rendering.

## Functional Components

### 1. Dropdown Menu

The dropdown menu is dynamically populated with the list of test subject IDs from the dataset. Users can select any ID, which triggers the dashboard to update with data for the selected individual.

### 2. Demographic Info Panel

The demographic information panel displays key metadata for the selected test subject. The `buildMetadata()` function fetches and filters this information from the dataset and appends each key-value pair as text to the HTML panel.

### 3. Bar Chart

The bar chart visualizes the top 10 OTUs found in each individual:

- **X-axis**: Represents the sample values (number of bacteria).
- **Y-axis**: Lists the top 10 OTU IDs in descending order.
- **Hover Text**: Shows the OTU labels when hovering over each bar.

### 4. Bubble Chart

The bubble chart visualizes all OTUs for the selected individual:

- **X-axis**: Represents the OTU IDs.
- **Y-axis**: Represents the sample values.
- **Marker Size**: Represents the sample values (larger bubbles indicate higher abundance).
- **Marker Color**: Each OTU ID has a unique color, and the colorscale used is "Earth".
- **Hover Text**: Shows OTU labels for each bubble.

### How the Code Works

1. **Data Loading**:

   - Data is loaded from the JSON file using D3.js.
   - The `init()` function initializes the dashboard with the first sample in the dropdown and populates the dropdown with sample IDs.

2. **Interactivity**:
   - **Dropdown Selection**: When a user selects a different test subject ID, the `optionChanged()` function triggers and updates both the charts and metadata.
   - **Demographic Panel**: The `buildMetadata()` function displays the demographic details in the metadata panel.
   - **Bar and Bubble Charts**: The `buildCharts()` function creates both charts based on the selected sample's data.

3. **Functions**:
   - `init()`: Initializes the dashboard by loading the first sample and populating the dropdown.
   - `optionChanged(newSample)`: Called whenever a new sample is selected; updates metadata and charts.
   - `buildMetadata(sample)`: Fetches and displays demographic data for the selected sample.
   - `buildCharts(sample)`: Creates the bar and bubble charts for the selected sample's data.

## Deployment

The project is deployed via GitHub Pages and can be accessed here:

- **Deployed Application**: [Belly Button Biodiversity Dashboard](https://rinals.github.io/belly-button-challenge/)
- **GitHub Repository**: [GitHub Repo](https://github.com/rinals/belly-button-challenge)
