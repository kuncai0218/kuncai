---
layout: default
title: TourGuideApp — Global attractions with ratings (Android + ArcGIS Runtime)
description: An Android app that lets travelers search the map, view authoritative attractions, add custom POIs, and submit 1–5 ratings with comments. Backed by AWS API Gateway + Lambda and PostgreSQL; front end built with ArcGIS Runtime SDK for Android.
---

Project name
TourGuideApp (Android)

Links
Source repository: https://github.com/kuncai0218/TourGuideApp
Demo video (YouTube): https://www.youtube.com/watch?v=T5Yvetkjbb4

Documentation
Executive report PDF: ../assets/docs/GlobalTourGuide_Summary.pdf

Screenshot (click to open the full image)
[![Main UI screenshot](../assets/img/tourguideapp-main.jpg "Alt: Android map UI with search box, zoom FABs, current location, OSM basemap, and buttons for Add Attraction and Top Attractions.")](../assets/img/tourguideapp-main.jpg)

Inline video preview
<iframe width="100%" height="420" src="https://www.youtube.com/embed/T5Yvetkjbb4" title="TourGuideApp — final demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>

Goal and audience
Give travelers a global, map-first way to compare attractions consistently across cities, add their own points of interest, and crowd-source ratings and comments that are tied to precise locations. Primary users are visitors and trip organizers; destination managers are a secondary audience who benefit from standardized, georeferenced feedback. :contentReference[oaicite:0]{index=0}

Mobile app features (Android, Kotlin)
1) OSM-based map with current location, zoom controls, and a global search box powered by ArcGIS World Geocoding.  
2) Loads an attractions FeatureLayer and opens callouts with attributes and website links; provides buttons to add reviews and view average rating and counts.  
3) Add Attraction flow lets users tap the map, enter name/type/description/URL, and post a structured JSON payload to the API; the new POI appears immediately on the map.  
4) Top Attractions panel requests ranked results from the API and recenters the map to a selected POI.  
5) Clean UI built with XML layouts and Material buttons/FABs; asynchronous requests keep the experience smooth. :contentReference[oaicite:1]{index=1}

Back-end and data architecture
Serverless REST API on AWS API Gateway with Node.js Lambda functions for addAttraction, submitReview, listAttractions, getAttractionById, and getTopAttractions; data persists in Amazon RDS PostgreSQL (extensible to PostGIS). Two core tables are used: attraction (id, name, description, tourism type, website, lat, lon, created_at) and reviews (id, attraction_id, rating 1.0–5.0, comment). Modular functions simplify maintenance and scaling; security and CORS are managed at the gateway. :contentReference[oaicite:2]{index=2}

Android code reference (high level)
MainActivity initializes ArcGISMap with a Streets basemap, sets an initial Viewpoint, adds a FeatureLayer from a ServiceFeatureTable, wires a LocatorTask for geocoding, and binds search and zoom controls; the mapScale is adjusted via setViewpointScaleAsync for zoom in/out. :contentReference[oaicite:3]{index=3}

Results
The app supports a complete “search → inspect → review → compare” loop on mobile. Users can jump to any place by name, open authoritative attributes, contribute ratings and comments, add custom POIs, and browse a ranked list to plan itineraries. :contentReference[oaicite:4]{index=4}

Deliverables recorded in this portfolio
Source repository: https://github.com/kuncai0218/TourGuideApp  
Executive report: ../assets/docs/GlobalTourGuide_Summary.pdf  
Main UI screenshot: ../assets/img/tourguideapp-main.jpg  
Demo video: https://www.youtube.com/watch?v=T5Yvetkjbb4

Next steps
Add offline caching, lightweight transit or routing integration, user authentication, spam-resistant moderation, and analytics for emerging tourist patterns; extend the schema to other domains such as events or restaurants. :contentReference[oaicite:5]{index=5}

Back link
Return to home page: ../index.md
