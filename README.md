# Eastern_Fox_Squirrels.aprx

This ArcGIS project file contains the Squirrel Surveys map with all the layers used in spatial data analysis. The coordinate system is WGS 1984 Web Mercator (auxiliary sphere). 
The project contains 9 layers: 
- **Morning_Sightings**	
Point layer with points representing each unqiue squirrel sighting on morning transects.
- **Morning_Transect_Lines**		
Line layer with lines representing routes walked during morning transect surveys.
- **Morning_Buffers**			
Polygon layer created using the buffer tool, representing the area within effective strip width around morning transects.
- **Morning_Buffers_w_Trees**	
Polygon layer of morning transect buffers with number of trees within buffers joined.
- **Morning_Buffers_w_Oaks**	
Polygon layer of morning transect buffers with number of oak (*Quercus* sp.) trees within buffers joined.
- **Evening_Sightings**	
Point layer with points representing each unqiue squirrel sighting on evening transects.
- **Evening_Transect_Lines**
Line layer with lines representing routes walked during evening transect surveys.
- **Evening_Buffers**	
Polygon layer created using the buffer tool, representing the area within effective strip width around evening transects.
- **Evening_Buffers_w_Trees**
Polygon layer of evening transect buffers with number of trees within buffers joined.
- **Evening_Buffers_w_Oaks**
Polygon layer of evening transect buffers with number of oak (*Quercus* sp.) trees within buffers joined.
- **Squirrel_Survey**
Original point layer from ArcGIS Field Maps with squirrel sightings entered in the field, including duplicate observations of same individuals.
- **New Tree Inventory**
Web-hosted point layer with geographic location, species identification, measurements, and other parameters for trees on Texas A&M's College Station campus collected during or after 2019.
- **Old Tree Inventory**		
Web-hosted point layer with geographic location, species identification, measurements, and other parameters for trees on Texas A&M's College Station campus collected before 2019.
- **Merged_Trees**
Point layer resulting from merging New Tree Inventory and Old Tree Inventory.
- **Quercus_Only**
Point layer resulting from using Select By Attribute on Merged_Trees to export only the oak (*Quercus* sp.) trees to the layer.

Descriptions of the fields in each layer are below.

### Morning_Sightings
|Field          |Description|
|---------------|---|
|OBJECTID_1*    |Unique ID number for each point|
|Shape*	        |Type of vector geometry (Point for all features in this layer)|
|Date.Time	    |The date and time (Hour:Minute:Seconds AM/PM) when the squirrel was seen|
|Temperature    |Temperature in degrees Fahrenheit, as reported in Apple Weather at the time the squirrel was seen|
|Species		|Species of the closest tree to the squirrel. Elm = Ulmus spp., Live = Quercus virginiana, Post = Quercus stellata, Othr = a different species/taxon|
|Notes	        |Comments on the sighting|
|x		        |Longitude in degrees|
|y	            |Latitude in degrees|
|Date	    	|Day of the month (in June, 2024) when the squirrel was seen|
|Time       	|Time in hours (0 to 24) when the squirrel was seen|
|Hour	    	|Hour of the day (rounding down) when the squirrel was seen|
|Minutes    	|Minutes after the hour when the squirrel was seen|
|Time.Frame	    |Half-hour block during which the squirrel was seen. Half hour blocks starting halfway between two hours end in .5 .|

### Morning_Transect_Lines
|Field			    |Description|
|-------------------|---|
|OBJECTID*	    	|Unique number for each transect line, with each line generally representing the distance walked within a half-hour time period block.
|Shape*	        	|Polyline M for all features in this layer
|Strip_width	    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line
|Date 	        	|Day on which the transect was walked
|Hour	            |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)|
|Shape_length       |Length in meters of the transect line (planar distance)|
|Transect_length    |Geodesic length of the transect in kilometers|

### Morning_Buffers
|Field			|Description|
|---------------|---|
|OBJECTID*      |Unique ID number for each buffer polygon|
|Shape*         |Geometry type (polygon for all features in this layer)|
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line|
|Date           |Day on which the transect was walked|
|Hour           |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)|
|Transect_length|Geodesic length of the transect (**not** length of the buffer polygon) in kilometers|
|BUFF_DIST      |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line, as used by Buffer tool to construct the polygons|
|Shape_Length   |Length in meters of the transect line (planar distance)|
|Shape_Area     |Area of the buffer polygon in planar square meters|

### Morning_Buffers_w_Trees
|Field		|Description|
|---------------|---|
|OBJECTID*      |Unique ID number for each buffer polygon|
|Shape*         |Geometry type (polygon for all features in this layer)|
|Join_Count     |Number of trees within the transect buffer, found using the Spatial Join tool|
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line|
|Date           |Day on which the transect was walked|
|Hour           |Half-hour block during which the transect was walked. 
|BUFF_DIST      |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line, as used by Buffer tool to construct the polygons|
|Shape_Length   |Length in meters of the transect line (planar distance)|
|Shape_Area     |Area of the buffer polygon in planar square meters|

### Morning_Buffers_w_Oaks
|Field 		|Description|
|---------------|---|
|OBJECTID*      |Unique ID number for each buffer polygon|
|Shape*         |Geometry type (polygon for all features in this layer)|
|Join_Count     |Number of oak (*Quercus* sp.) trees within the transect buffer, found using the Spatial Join tool|
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line|
|Date           |Day on which the transect was walked|
|Hour           |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)|
|Transect_length|Geodesic length of the transect (**not** length of the buffer polygon) in kilometers|
|BUFF_DIST      |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line, as used by Buffer tool to construct the polygons|
|Shape_Length   |Length in meters of the transect line (planar distance)|
|Shape_Area     |Area of the buffer polygon in planar square meters|
|Buffer_area    |Area of the buffer polygon in geodesic square kilometers, as calculated by the Calculate Geometric Attributes tool|

### Evening_Sightings
|Field		|Description|
|-----------|--------------|
|OBJECTID_1*|Unique ID number for each point
|Shape	    |Type of vector geometry (Point for all features in this layer)
|Date.Time	|The date and time (Hour:Minute:Seconds AM/PM) when the squirrel was seen
|Temperature|Temperature in degrees Fahrenheit, as reported in Apple Weather at the time the squirrel was seen
|Species	|Species of the closest tree to the squirrel. Elm = Ulmus spp., Live = Quercus virginiana, Post = Quercus stellata, Othr = a different species/taxon
|Notes		|Comments on the sighting
|x			|Longitude in degrees
|y			|Latitude in degrees
|Date		|Day of the month (in June, 2024) when the squirrel was seen
|Time		|Time in hours (0 to 24) when the squirrel was seen
|Hour		|Hour of the day (rounding down) when the squirrel was seen
|Minutes	|Minutes after the hour when the squirrel was seen
|Time.Frame	|Half-hour block during which the squirrel was seen. Half hour blocks starting halfway between two hours end in .5 .

### Evening_Transect_Lines
|Field	       	|Description|
|---------------|-----------|
|OBJECTID*	    |Unique number for each transect line, with each line generally representing the distance walked within a half-hour time period block.
|Shape*		    |Polyline M for all features in this layer
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line
|Date 		    |Day on which the transect was walked
|Hour		    |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)
|Transect_length|Geodesic length of the transect in kilometers

### Evening_Buffers
|Field		    |Description|
|---------------|-----------|
|OBJECTID*      |Unique ID number for each buffer polygon|
|Shape*         |Geometry type (polygon for all features in this layer)|
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line|
|Date           |Day on which the transect was walked|
|Hour           |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)|
|Transect_length|Geodesic length of the transect (**not** length of the buffer polygon) in kilometers|
|BUFF_DIST      |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line, as used by Buffer tool to construct the polygons|

### Evening_Buffers_w_Trees
|Field			|Description|
|---------------|-----------|
|OBJECTID*      |Unique ID number for each buffer polygon|
|Shape*         |Geometry type (polygon for all features in this layer)|
|Join_Count     |Number of trees within the transect buffer, found using the Spatial Join tool|
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line|
|Date           |Day on which the transect was walked|
|Hour           |Half-hour block during which the transect was walked. 
|BUFF_DIST      |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line, as used by Buffer tool to construct the polygons|

### Evening_Buffers_w_Oaks
|Field 			|Description|
|---------------|-----------|
|OBJECTID*      |Unique ID number for each buffer polygon|
|Shape*         |Geometry type (polygon for all features in this layer)|
|Join_Count     |Number of oak (*Quercus* sp.) trees within the transect buffer, found using the Spatial Join tool|
|Strip_width    |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line|
|Date           |Day on which the transect was walked|
|Hour           |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)|
|Transect_length|Geodesic length of the transect (**not** length of the buffer polygon) in kilometers|
|BUFF_DIST      |Effective strip width in meters: distance to farthest squirrel from the transect line or maximum visibility to either side of the transect line, as used by Buffer tool to construct the polygons|
|Buffer_area| Area of the buffer polygon in geodesic square kilometers, as calculated by the Calculate Geometric Attributes tool|


### Squirrel_Survey
|Field					        |Decription|
|-------------------------------|----------|
|OBJECTID *|Unique ID number for each squirrel sighting point|
|Position source type|Integrated (System) Location Provider, Snapped, or User defined|
|Notes|Comments on squirrel sighting, including correct time for data points originally collected without Field Maps and entered in the app later on
|Date/Time|Date and time in mm/dd/yyyy hh:mm:ss AM/PM format. Date and time listed here are incorrect for data points entered into Field Maps after-the-fact.
|Temperature|Temperature in degrees Fahrenheit at the time of the sighting, as reported in the Apple Weather app
|Cloud cover (%)|Approximate percent cloud cover at the time and location of the sighting, rounded to 0, 25, 50, 75, or 100%
|Species|Species of tree closest to the squirrel, as identified in the field. "Other" represents tree species that was not an option in the Field Maps drop-down menu.
|Canopy cover (%)|Percent of area directly above the squirrel at time and location of sighting covered by tree canopy, reported as categorical ranges: 0-25%, 25-50%, 50-75%, or 75-100%
|Behavior|Categorical behavior at the time of the sighting: Eating (for foraging or feeding), Interaction (between 2 or more squirrels), Nest only (for points representing a squirrel nest, but not an actual squirrel sighting), Nest-building, Resting, and Traveling (any active movement not during obvious foraging or feeding) 
|Substrate/surface|Asphalt/street, Bare ground/dirt, Concreete/sidewalk (for paved surface other than a street), Grass, Mulch, Other, or Tree
|Shape|Geometry type of the feature (Point M for all features in this layer)
### New Tree Inventory
### Old Tree Inventory
Descriptions of the New Tree Inventory and Old Tree Inventory layers are available here: https://services1.arcgis.com/qr14biwnHA6Vis6l/arcgis/rest/services/Aggie_Trees_Map_Official/FeatureServer
### Merged_Trees
Resulting vector layer of points from merging New Tree Inventory and Old Tree Inventory. Symbology shows which trees are oaks (*Quercus* sp.) and which are not.
### Quercus_Only
Resulting vector layer of points exported after Select by Attribute on Merged_Trees, selecting for Genus EQUALS Quercus. This layer contains only oak (*Quercus* sp.) trees.

# Whitman_Werdel_2024_code.R
R file containing all the code needed to reproduce the statistical analysis of the paper. 

# Whitman_Werdel_2024_code.Rmd
R Markdown file contaoning all the code needed to reproduce the statistical analysis of the paper.

# whitman_werdel_fox_squirrel_code.R
This R file contains all the code needed to reproduce the statistical analysis of the paper.

# Squirrel_Survey.csv
This csv file contains the original squirrel sightings data recorded in ArcGIS Field Maps. Some time stamps have been corrected for data points originally recorded out of Field Maps on the evening of the 16th and entered at the geographic location in Field Maps on July 20th or 21st.

|Column				              |Decription|
|-------------------------------|----------|
|OBJECTID                       |Unique ID number for each squirrel sighting point
|Date/Time                      |Date and time in mm/dd/yyyy hh:mm:ss AM/PM format. Date and time listed here are incorrect for data points entered into Field Maps after-the-fact.
|Temperature                    |Temperature in degrees Fahrenheit at the time of the sighting, as reported in the Apple Weather app
|Cloud cover (%)                |Approximate percent cloud cover at the time and location of the sighting, rounded to 0, 25, 50, 75, or 100%
|Species                        |Species of tree closest to the squirrel, as identified in the field. "Other" represents tree species that was not an option in the Field Maps drop-down menu.
|Canopy cover (%)               |Percent of area directly above the squirrel at time and location of sighting covered by tree canopy, reported as categorical ranges: 0-25%, 25-50%, 50-75%, or 75-100%.
|Behavior                       |Categorical behavior at the time of the sighting: Eating (for foraging or feeding), Interaction (between 2 or more squirrels), Nest only (for points representing a squirrel nest, but not an actual squirrel sighting), Nest-building, Resting, and Traveling (any active movement not during obvious foraging or feeding)
|Substrate/surface              |Asphalt/street, Bare ground/dirt, Concreete/sidewalk (for paved surface other than a street), Grass, Mulch, Other, or Tree
|Notes                          |Comments on squirrel sighting, including correct time for data points originally collected without Field Maps and entered in the app later on
|x                              |Decimal latitude of the squirrel's location
|y                              |Decimal longitude of the squirrel's location
|duplicate                      |"yes" if the observation is of the same squirrel already observed before during the same transect.

# all_transects.csv
This csv file contains parameters, both those recorded in the field and those estimated using ArcGIS Pro, for all transects, as needed to run the statistical analysis in R.

|Column				              |Decription|
|-------------------------------|----------|
|date                           |Day of the month when the transect was conducted.
|hour                           |Half-hour block during which the transect was walked. Half hour blocks starting halfway between two hours end in .5 (e.g. transect walked between 8:30 a.m. and 9:00 a.m. is designated 8.5)
|time.of.day                    |Categorical time of day during which the transect was conducted: early morning (7:00 A.M. - 9:30 A.M.), late morning (9:30 A.M. - 12:00 P.M.), early evening (5:00 P.M. - 6:30 P.M.), or late evening (6:30 P.M. - 8:00 P.M.)
|dur.min                        |The number of minutes spent actively looking for squirrels during the half-hour block in which the transect occured|
|min.T.degrees.F                |The lowest temperature recorded from Apple Weather during the given transect, in degrees Fahrenheit. 
|min.T.degrees.C                |The same information but converted to degrees Celsius. 
|estimated.min.T.degrees.F      |Estimated temperature in degrees Fanhrenheit for transects on which no squirrels were seen, and temperatures was never recorded. (This data is the same as 'min.T.degrees.F' for transects where temperatures were recorded in the field.) 
|estimated.min.T.degrees.C      |The same information but converted to degrees Celsius. 
|max.T.degrees.F                |The maximum temeprature recorded along the transect, in degrees Fanhrenheit. 
|max.T.degrees.C                |The same information but converted to degrees Celsius.
|num.squir                      |Number of individual squirrels counted along the transect
|squir.dens.sq.km               |Number of squirrels per square kilometers within the area observed along the transect.
|length.km                      |Distance walked along the transect in kilometers
|area.sq.km                     |Area of the round-ended buffer polygon around the transect, representing the observable area within effective strip width of the transect, as calculated in ArcGIS Pro by Calculate Geometric Attributes
|num.trees                      |Number of trees in the merged Aggie Tree Layer within the effective strip width along the transect.
|tree.dens.sq.km                |Density of trees per square kilometer within the effective strip width along the transect.
|num.oaks                       |Number of oak trees (*Quercus* spp.) in the merged Aggie Tree Layer within the effective strip width along the transect.
|oak.density.sq.km              |Density of oak trees (*Quercus* spp.) per square kilometer within the effective strip width along the transect.
|buff.distance.m.planar         |One-sided effective strip width in meters along the transect.

# trees_by_species.csv
This csv file contains the number of trees by species within the effective strip width of all transects combined. This was generated in ArcGIS Pro by duplicating, merging, and dissolving the transect buffer layers and then using the Spatial Join tool, with Join Operaton as Join one to many and Match Option as Intersect, to export all trees within the buffer area to a new layer, which was exported as an xlsx file using Table To Excel. This data was imported to R, trees were summarized by species, and this was exported to the tree_by_species.csv file. Duplicate rows by species were combined by hand. If a genus contained several species, these were summed and placed in a new row with the total number of trees per genus.

# squirrels_in_trees.csv
This csv file is a duplicate of the original Squirrel_Survey.csv file but only contains unique individual observations of squirrels that were in trees.

# squirrels_near_trees.csv
This csv file is a duplicate of the original Squirrel_Survey.csv file, but duplicate observations of the same squirrel near the same tree at the same time are marked as "yes" in the column "duplicate".


 
