---
layout: default
title: Asthma Research Database — GEOG 574 (2014–2018)
description: A database-driven public health GIS project integrating CDC asthma prevalence with EPA air-quality indicators using PostgreSQL/PostGIS and ArcGIS Pro to reveal patterns, trade-offs, and changes over time.
---

Project name
Asthma Research Database

Course and team
GEOG 574: Geospatial Database Design and Development. Team: Maria De Fatima Alejo and Kun Cai.

My role
Database design and implementation in PostgreSQL/PostGIS; schema normalization for state and year dimensions; ETL of CDC asthma, EPA AQI, and state population CSVs; creation of analytical views; cartographic visualization in ArcGIS Pro; results interpretation and write-up.

Objective
Integrate CDC state-year asthma prevalence with EPA state-year air quality metrics and derive indicators that answer five questions: where asthma is highest, where high asthma coexists with clean air, where low asthma coexists with polluted air, which states changed the most over time, and what factors may explain those changes.

Data and sources
CDC current-asthma prevalence by state and year; EPA AQI summaries by state and year including Days with AQI, Good/Moderate/Unhealthy/Very Unhealthy/Hazardous categories and Median AQI; optional state population per year. Indicators follow WHO guidance on pollutants such as PM2.5, ozone, and NO2. Details match the final report. 

Links
Download the final paper PDF: [../assets/docs/GEOG574-Asthma-Research.pdf](../assets/docs/GEOG574-Asthma-Research.pdf)

Inline PDF preview
<iframe src="../assets/docs/GEOG574-Asthma-Research.pdf" title="Asthma Research Database — final paper" width="100%" height="560" loading="lazy" style="border:1px solid #ddd;border-radius:8px;"></iframe>

Stack
PostgreSQL 14+ (with or without PostGIS for this analysis), psql \copy for bulk loads, SQL views for analytics, ArcGIS Pro for maps and charts.

Database design (concise)
1) Dimensions: state(text primary key) and year(smallint, 1900–2100 check).  
2) Facts: cdc_asthma_2014_2018(State, Year, Number with Current Asthma, Percent with Current Asthma); epa_aqi_all_data(State, Year, category counts, Max/90th/Median AQI, pollutant-day counts); Est_POP_ST_2014_2018(State, Year, Population).  
3) Foreign keys: facts reference the state and year dimensions.  
4) Core view v_state_year: left-join CDC, EPA, Population per State–Year and derive good_days_pct = Good Days / Days with AQI * 100.  
5) Quality views: v_state_year_any keeps rows with all key metrics present (2014–2018); v_state_avg_any computes per-state averages; v_state_deltas_any computes endpoint deltas for asthma_pct, median_aqi, and good_days_pct to rank changes.  
The schema, loading scripts, and queries are summarized from the paper. 

Method
Create normalized reference tables for states and years; bulk-load cleaned CSVs; seed distinct states/years; add foreign keys; build views to avoid repeating joins; write five query families: top asthma with corresponding AQI; high-asthma and good-air (upper-quartile asthma intersect lower-quartile AQI); low-asthma and bad-air (lower-quartile asthma intersect upper-quartile AQI); and two “drastic change” leaderboards based on endpoint deltas for asthma and AQI. 

Results (headline findings mirrored from the paper)
Highest average asthma: West Virginia about 11.8% with an average median AQI near 38.8.  
Close followers: New Hampshire 11.62% (AQI ~38.6) and Maine 11.48% (AQI ~36.2).  
High asthma with clean air: Vermont about 11.2% while average median AQI is ~32.6 (bottom quartile AQI, top-decile asthma).  
Bad air with low asthma: California ~7.82% with AQI ~52.4; Georgia ~8.56% with AQI ~44.0; Iowa ~8.5% with AQI ~43.6.  
Largest variability over time (2014–2018): New Hampshire shows the widest asthma swings (≈ ±3 points), Nevada next (≈ ±2.5); for AQI, Puerto Rico ≈ ±12 and Rhode Island ≈ ±8.  
These numbers and thresholds come from the final submission. 

Maps and visuals
Choropleths and ranking tables produced in ArcGIS Pro using the state-level outputs from the SQL views; quartile cuts for good air vs. bad air and high vs. low asthma drive bivariate highlights.

Limitations and next steps
Adopt GlobalID/GUID keys and enforce CDC/EPA state name canonicalization; add uncertainty bands; extend time range beyond 2018; control for confounders (age, smoking, insurance, urbanization) with regression; publish an interactive dashboard that lets users filter by pollutant family and year range.

Deliverables recorded in this portfolio
Final paper: [../assets/docs/GEOG574-Asthma-Research.pdf](../assets/docs/GEOG574-Asthma-Research.pdf)

Back link
Return to home page: ../index.md
