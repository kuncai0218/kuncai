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
Executive report PDF: [{{ site.baseurl }}/assets/docs/GlobalTourGuide_Summary.pdf]({{ site.baseurl }}/assets/docs/GlobalTourGuide_Summary.pdf)

Screenshot (click to open the full image)
[![Main UI screenshot]({{ site.baseurl }}/assets/img/tourguideapp-main.jpg "Alt: Android map UI with search box, zoom FABs, current location, OSM basemap, and buttons for Add Attraction and Top Attractions.")]({{ site.baseurl }}/assets/img/tourguideapp-main.jpg)

Inline video preview
<iframe width="100%" height="420" src="https://www.youtube.com/embed/T5Yvetkjbb4" title="TourGuideApp — final demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen loading="lazy"></iframe>

Goal and audience
Give travelers a global, map-first way to compare attractions consistently across cities, add their own points of interest, and crowd-source ratings and comments that are tied to precise locations. Primary users are visitors and trip organizers; destination managers are a secondary audience who benefit from standardized, georeferenced feedback.

Mobile app features (Android, Kotlin)
1) OSM-based map with current location, zoom controls, and a global search box powered by ArcGIS World Geocoding.
2) Loads an attractions FeatureLayer and opens callouts with attributes and website links; provides buttons to add reviews and view average rating and counts.
3) Add Attraction flow lets users tap the map, enter name/type/description/URL, and post to a serverless API; the new POI appears immediately on the map.
4) Top Attractions panel requests ranked results from the API and recenters the map to a selected POI.
5) Clean UI using Material components; asynchronous requests keep the experience smooth.

Back-end and data architecture
Serverless REST API on AWS API Gateway with Lambda functions (addAttraction, submitReview, listAttractions, getAttractionById, getTopAttractions). Data persists in Amazon RDS PostgreSQL. Tables: attraction(id, name, description, type, website, lat, lon, created_at) and reviews(id, attraction_id, rating, comment).

Android code reference (high level)
MainActivity initializes ArcGISMap, adds a ServiceFeatureTable as a FeatureLayer, wires a LocatorTask for geocoding, and binds search and zoom controls; mapScale adjustments use setViewpointScaleAsync.

Results
The app supports a complete search → inspect → review → compare loop on mobile, enabling georeferenced feedback and ranked browsing.

Deliverables recorded in this portfolio
Source repository: https://github.com/kuncai0218/TourGuideApp
Executive report: [{{ site.baseurl }}/assets/docs/GlobalTourGuide_Summary.pdf]({{ site.baseurl }}/assets/docs/GlobalTourGuide_Summary.pdf)
Main UI screenshot: {{ site.baseurl }}/assets/img/tourguideapp-main.jpg
Demo video: https://www.youtube.com/watch?v=T5Yvetkjbb4

Next steps
Add offline caching, routing, authentication, and spam-resistant moderation; extend analytics and categories.

Back link
Return to home page: {{ site.baseurl }}/index.md
