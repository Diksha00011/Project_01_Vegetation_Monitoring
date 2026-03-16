Vegetation Change Monitoring using Landsat NDVI and CHIRPS Rainfall

Overview:
This project builds a remote sensing workflow to detect vegetation change and its relationship with rainfall using long-term satellite observations.

The workflow integrates:
Landsat surface reflectance imagery (1984–present) for vegetation monitoring
CHIRPS rainfall data for climate analysis
Statistical trend detection methods including Sen’s slope and Mann-Kendall trend test
The pipeline generates NDVI maps, vegetation trend maps, rainfall analysis, and an integrated dashboard showing vegetation dynamics over time.

Objectives
The main goals of this project are:
Monitor long-term vegetation change
Identify vegetation degradation hotspots
Quantify NDVI–rainfall relationships
Produce analysis-ready geospatial outputs
Generate dashboard-style visualizations

Technologies Used:
Python
Google Colab
Rasterio
NumPy
Pandas
Matplotlib
SciPy

Data Sources
Landsat Satellite Data
Source: USGS Collection 2 Level-2 Surface Reflectance

Sensors used:
Landsat 5 (1984–2013)
Landsat 7 (1999–present)
Landsat 8 (2013–present)
Landsat 9 (2021–present)
Only January observations are used to reduce seasonal variability.
CHIRPS Rainfall Dataset
Climate Hazards Group InfraRed Precipitation with Station data

Characteristics:
Daily rainfall estimates
Global coverage
~5 km spatial resolution
Available from 1981 to present

Methodology
1. NDVI Computation
Vegetation health is estimated using the Normalized Difference Vegetation Index:
NDVI = (NIR − Red) / (NIR + Red)
Clouds and shadows are removed using Landsat QA masks.

2. Time-Series Construction
For each year:
January, February and March images are filtered
Median NDVI composite is generated
Images are clipped to the study area
These NDVI rasters form the multi-year NDVI stack.

3. Trend Analysis
Vegetation trends are estimated using two methods:

Sen’s Slope
Measures the rate of vegetation change over time.

Interpretation:
Negative slope → vegetation degradation
Near zero → stable vegetation
Positive slope → vegetation improvement

Mann-Kendall Test
A non-parametric statistical test used to evaluate trend significance.

4. Vegetation Change Classification
Pixels are classified into three categories:
Class	Description
1	Vegetation Degradation
2	Stable Vegetation
3	Vegetation Improvement
5. Rainfall Analysis

Annual rainfall is computed from the CHIRPS dataset.

The workflow calculates:
Mean annual rainfall
Rainfall time series
NDVI–rainfall correlation
R² coefficient

6. Visualization
The project produces several visual outputs:
NDVI maps for each year
NDVI time series plots
Rainfall time series
NDVI–rainfall scatter plots
Vegetation change pie charts
Trend distribution histograms
Mann-Kendall significance map
A combined vegetation monitoring dashboard summarizes all results.

Output Files

The workflow exports the following outputs:

NDVI Data
Landsat NDVI maps:
L5_January_YYYY.tif
L8_January_YYYY.tif
L9_January_YYYY.tif

Trend Analysis
Landsat_NDVI_SenSlope.tif
Landsat_MannKendall_Tau.tif
Landsat_Vegetation_Trend_Class.tif
Visualizations
NDVI_TimeSeries.png
NDVI_Variability.png
NDVI_Trend_Map.png
Trend_Distribution.png
Vegetation_Change_PieChart.png
MannKendall_Map.png
NDVI_Rainfall_Correlation.png
NDVI_Rainfall_Timeseries.png
Vegetation_Dashboard.png

Data Tables
NDVI_Rainfall_Table.csv
NDVI_Rainfall_Statistics.txt
Project Structure
Project_01_vegetation_Change

│
├── Landsat NDVI rasters
├── Trend analysis rasters
├── NDVI visualizations
├── Rainfall analysis outputs
└── Dashboard figures
Workflow Pipeline
Extract January Landsat imagery using Google Earth Engine
Compute NDVI and export raster files
Build NDVI time-series stack
Perform Sen’s slope and Mann-Kendall trend analysis
Classify vegetation change
Compute rainfall statistics from CHIRPS
Analyze NDVI–rainfall relationships
Generate dashboard visualizations

Applications
This workflow can be applied to:
Forest degradation monitoring
Climate change studies
Watershed vegetation analysis
Environmental impact assessments
Land management planning

Future Improvements
Possible enhancements include:
Landsat sensor harmonization
Seasonal NDVI analysis
Vegetation anomaly detection
Interactive web dashboards

Automated ROI selection
