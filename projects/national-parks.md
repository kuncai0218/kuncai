
Title
US Top 20 National Parks by Recreation Visits (2022)

Course and role
GEOG 370 final project. Role: end-to-end cartography, including data sourcing, processing, mapping, labeling, layout design, and export.

Tools
ArcGIS Pro for data processing and map composition. Adobe Illustrator for typography, spacing, callouts, and final poster polish.

Goal and audience
The goal is to communicate which U.S. national parks attracted the most visitors in 2022 and to make comparison quick and intuitive. The intended audience is the general public, park enthusiasts, and entry-level GIS learners who need a clear, publication-ready thematic map.

Outcome summary
A one-page poster map that ranks the twenty most-visited U.S. national parks. Quantity is encoded with graduated circles sized by annual recreation visits. For each park, a labeled callout presents the park name, a nearby city, the area, and the 2022 visits. The layout includes title, legend, scale, credits, data sources, and a projection note. A web preview image is provided for this portfolio page, and the print-quality PDF is available for download.

Data and sources
Visitation counts for 2022 were consolidated from the standard NPS and Wikipedia lists. U.S. state polygons were used as the basemap geography. The poster cites icon and image sources in the credits. Projection used: North America Albers Equal Area Conic, which preserves area for fair comparison across the country. 

File locations used in this page
Preview image path: ../assets/img/national-parks.jpg
Poster PDF path: ../assets/docs/national-parks-poster.pdf
Recommended alt text for the preview image: “Poster map of the United States showing the top 20 national parks by 2022 recreation visits using graduated circles, with named callouts, legend, scale bar, credits, and an Albers Equal Area projection.”

Method and workflow

Collect and clean. Compile a table of 2022 recreation visits. Standardize park names, states, and basic attributes. Add supporting fields such as a nearby city and park area.

Rank and select. Sort by visits in descending order and select the top twenty records.

Locate and validate. Obtain representative park points or centroids. Check that each location falls within the expected state polygon and fix any outliers.

Symbolization. Use graduated circles to encode total visits. Apply a square-root scaling to maintain contrast without letting a few parks dominate the visual. Keep the basemap very light so the symbols stand out.

Labeling and callouts. Create a callout for each park with park name, nearest city, area, and 2022 visits. Use a clear typographic hierarchy so names are most prominent, with supporting details in a smaller style.

Layout composition. Add title, subtitle, legend explaining circle sizes, scale bar, data sources, icon credits, and a projection note. Balance white space and align callouts to avoid collisions.

Export and QA. Export a vector PDF for print and a downsampled JPG for web. Do a final pass for spelling, unit consistency, and visual balance.

Design rationale
Equal-area projection avoids misleading area perception, which is important when comparing nationwide quantities. Graduated circles are a familiar and direct way to show totals for non-technical audiences. A restrained color palette and strong contrast improves readability. Typography is kept consistent so viewers can scan quickly from symbol to callout to legend. Alt text is provided for accessibility.

Results and insights
Great Smoky Mountains ranks first with roughly 12.9 million visits. Grand Canyon and Zion each receive well over 4.6 million visits, and Yellowstone is around 3.29 million. There is a clear concentration through the Utah–Arizona corridor, and urban-adjacent parks such as Cuyahoga Valley and Gateway Arch benefit from easy accessibility. The distribution is right-skewed, meaning a small number of parks capture a large share of total visits. These headline numbers and the projection choice match the finished poster. 

Deliverables in this portfolio
Poster for download: ../assets/docs/national-parks-poster.pdf
Web preview image used on this page: ../assets/img/national-parks.jpg
If needed, an interactive version can later be added with an ArcGIS Online iframe and a year selector.

Reflection and next steps
What worked well: a simple ranking story, clear symbolization, and a print-ready layout with consistent typographic hierarchy.
Improvements to make next: standardize all areas to square kilometers, proofread diacritics and long names, tighten leader lines and callout spacing.
Future work: publish an interactive web version that updates yearly with the latest NPS statistics and adds quick filters for region or state.

Back link for navigation
Return to home page: ../index.md
