---
layout: default
title: GEOG 578 — Spatial Analysis of Public Health Resource Accessibility in Dane County
description: Tract-level healthcare accessibility in Dane County using a ring-buffer score, network distance to the nearest facility, and correlations with income and insurance coverage.
---

Project name
Spatial Analysis of Public Health Resource Accessibility in Dane County

Course and date
GEOG 578 GIS Applications. May 2, 2025.

Instructor
William Gartner.

Author
Kun Cai.

Capstone statement
This project measures tract-level disparities in healthcare accessibility across Dane County by combining a distance-weighted multi-ring buffer score and network driving distance to the nearest hospital or clinic, and then relates these measures to median household income and insurance coverage. :contentReference[oaicite:0]{index=0}

Objective
Evaluate whether unequal access is primarily geographic (distance and facility distribution) or socio-economic (income and uninsurance), and provide evidence that can guide more equitable siting or transport interventions. :contentReference[oaicite:1]{index=1}

Links
Download the paper PDF: [../assets/docs/GEOG578-Health-Accessibility-Dane-County.pdf](../assets/docs/GEOG578-Health-Accessibility-Dane-County.pdf)

Inline PDF preview
<iframe src="../assets/docs/GEOG578-Health-Accessibility-Dane-County.pdf" title="GEOG 578 — Dane County accessibility paper" width="100%" height="560" loading="lazy" style="border:1px solid #ddd;border-radius:8px;"></iframe>

Study area and data
Unit of analysis is the census tract (n ≈ 125). Tract polygons were joined to ACS tables for income and insurance coverage. Medical facilities were extracted via Overpass Turbo (amenity=hospital|clinic and healthcare=urgent_care|health_care). A 10-mile buffer around the county boundary retained cross-border facilities; OSM road centerlines support a Network Dataset for driving distance. :contentReference[oaicite:2]{index=2}

Accessibility score: multi-ring buffer method
Five concentric rings (2, 4, 6, 8, 10 miles) around each facility implement distance decay and differential capacity. Hospitals are scored 10, 8, 6, 4, 2 by ring; clinics 5, 4, 3, 2, 1. Hospital and clinic buffer surfaces are dissolved and stacked; tract centroids intersect the composite surface and inherit the summed score, then joined back to tracts. Distances are measured in NAD 1983 HARN Wisconsin South. :contentReference[oaicite:3]{index=3}

Network distance to nearest facility
Using ArcGIS Network Analyst Closest Facility, each tract centroid routes along OSM roads to its nearest hospital or clinic; the result is a one-way road distance in miles (Miles_route). This captures bridges, cul-de-sacs, and water barriers that straight-line buffers miss. :contentReference[oaicite:4]{index=4}

Correlation analysis
A cleaned table (invalid placeholders removed) computes Pearson’s r among four variables: accessibility score, Miles_route, uninsurance rate, and median household income, producing a 4×4 correlation matrix for hypothesis checks about spatial-social disadvantage. :contentReference[oaicite:5]{index=5}

Results and interpretation
A strong negative correlation appears between accessibility score and network distance (r ≈ −0.60), confirming internal consistency: tracts farther from providers score lower. Correlations between access and income or uninsurance are weak, reflecting the Dane County pattern where central Madison tracts can be low-income yet highly accessible, while some higher-income outer tracts are far from care. Policy context and tract heterogeneity may further weaken simple socio-economic correlations. Overall, access disparities are chiefly geographic here. :contentReference[oaicite:6]{index=6}

Implications
Target rural and edge tracts with long drives for new clinics, mobile services, telemedicine, or transport improvements; maintain strong central-city coverage while addressing periphery gaps. :contentReference[oaicite:7]{index=7}

Limitations and next steps
Extend the temporal range beyond 2018, test broader regions, control for potential confounders (age, smoking, insurance type, urbanization), and consider 2SFCA or E2SFCA in parallel with distance methods. :contentReference[oaicite:8]{index=8}

Back link
Return to home page: ../index.md
