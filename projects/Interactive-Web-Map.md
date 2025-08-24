---
layout: default
title: Interactive Web Map — Add and Rate Attractions (ArcGIS JS 4.24)
description: A mobile-friendly web map that lets users add attractions and leave comments/ratings. Built with ArcGIS JavaScript API 4.24 using FeatureLayer editing, custom popups, Search/Locate widgets, and a toggleable legend.
---

Project name
Add and Rate Attractions (Madison, WI)

Links
Live map: https://kuncai0218.github.io/Midtermproject_KunCai/
Source repository: https://github.com/kuncai0218/Midtermproject_KunCai

Screenshot (click to open)
[![App screenshot](../assets/img/Interactive-Web-Map.jpg "Alt: Madison basemap with custom and OSM attractions. Popup shows fields plus buttons to add a comment or rating; legend on the left; Search and Locate at top-left; Add my attraction button at top-right.")](https://kuncai0218.github.io/Midtermproject_KunCai/)

Inline preview (iframe)
<iframe src="https://kuncai0218.github.io/Midtermproject_KunCai/" title="Interactive Web Map — live demo" width="100%" height="560" loading="lazy" style="border:1px solid #ddd;border-radius:8px;"></iframe>

Goal and audience
Create a mobile-friendly web map where viewers can add their own attractions and contribute comments and 1–5 ratings while browsing existing OSM points. Target users are city visitors and students learning practical web-GIS editing patterns.

Stack and services
ArcGIS JavaScript API 4.24; Map and MapView; FeatureLayer applyEdits and queryFeatures; Popup with custom DOM; Legend; Search; Locate.  
Feature services configured in the app: an OSM attractions layer, an editable My_Attraction layer for user points, and a Comments_and_Rating layer for feedback.

Key features and workflow
1) Add-my-attraction button toggles an editing mode. Clicking the map opens a floating form for name, type, and description; Submit writes to the editable layer via applyEdits; Cancel exits editing and restores UI state.  
2) Click behavior: when editing is off, a hitTest on OSM and user layers opens a docked popup for the clicked feature.  
3) Popup actions: custom buttons Add Comment and Add Rating create Graphics and write to the feedback layer; loadComments then queries related feedback and shows a feed with an average rating.  
4) Search and Locate widgets help users find places and their current position.  
5) Legend in a custom panel with a Show/Hide toggle to maximize viewport on small screens.  
6) Accessibility and UX: strong color contrast for the add button; informative titles and alt text; docked popups for stable reading.

Data model notes
AttractionID links comments and ratings to a feature. For production, replace name-based linking with GlobalID or GUID to prevent collisions and support robust joins.

Quality and performance
Simple symbolization keeps rendering fast; client-side average avoids extra server load. Inputs restrict rating to the 1–5 range. Production hardening would add stricter validation, XSS-safe text handling, and authentication.

Deliverables recorded in this portfolio
Live app: https://kuncai0218.github.io/Midtermproject_KunCai/  
Source code: https://github.com/kuncai0218/Midtermproject_KunCai  
Screenshot asset used on this page: ../assets/img/attractions-app.jpg

Next steps
Add photo attachments; clustering for dense areas; type filters; store the average rating with an Arcade expression or a layer view; sign-in to attribute comments to verified users.

Back link
Return to home page: ../index.md
