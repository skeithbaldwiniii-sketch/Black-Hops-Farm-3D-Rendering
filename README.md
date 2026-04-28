# Black-Hops-Farm-3D-Rendering
## 3D Farm Modeling & DSM Creation (Lucketts, Loudoun County, VA)
This project focuses on building a 3D model of a working farm by integrating multiple geospatial datasets and generating a Digital Surface Model (DSM) for visualization and physical modeling.

This was my final project in the GIS 3-Dimensional Analysis course at Northern Virginia Community College, completed in May 2025. I chose this site because it was the farm where I was working at the time, which made it a good opportunity to connect GIS work to a real-world location I was familiar with.

## Data Collection & Preparation
I started with publicly available data from the Loudoun GeoHub, including parcels, buildings, forest cover, trees, water bodies, and road layers. I isolated the farm parcel and clipped each dataset down to the area of interest to keep everything focused and manageable.

<img width="550" height="296" alt="Screenshot 2025-04-12 173855" src="https://github.com/user-attachments/assets/377ffca3-5f28-4bed-aedc-70b1da9d0fb4" />

I also downloaded a DEM from Earth Explorer, which would later be used as the base elevation surface.

## Feature Processing

To prepare the data for 3D modeling, I needed to assign height values to different features:

- Buildings were manually assigned heights using attribute fields
  
- One building required splitting into multiple sections to reflect different roof heights
 <img width="550" height="300" alt="Screenshot 2025-04-12 180628" src="https://github.com/user-attachments/assets/01cdd4be-5ebe-405a-8b75-72916a36b744" />
 
- Trees were standardized to 8 meters
  
- Forest areas were set to 1 meter
  
- Roads and water features were set to 0.5 meters to maintain visibility in the final surface
<img width="275" height="300" alt="Screenshot 2025-04-12 193136" src="https://github.com/user-attachments/assets/dc34d2a3-0be2-4181-ae1f-811408944a5a" />

Since the merge tool requires consistent geometry types, I converted the tree points into polygons using a buffer so they could be combined with the other layers.


<img width="275" height="300" alt="Screenshot 2025-04-16 223151" src="https://github.com/user-attachments/assets/5f89586d-8e81-4e22-b9a5-bf4831fd533d" />

All features were then merged into a single polygon dataset to streamline processing.

<img width="275" height="300" alt="Screenshot 2025-04-12 191959" src="https://github.com/user-attachments/assets/78012d82-af1b-42be-932e-2bf973e21364" />

<img width="442" height="373" alt="Screenshot 2025-04-23 202820" src="https://github.com/user-attachments/assets/caa5df3c-62c0-4c22-af75-20ec9a837f93" />




## Raster Conversion & DSM Creation

The merged polygon layer was converted into a raster so it could be combined with the DEM.

<img width="275" height="273" alt="Screenshot 2025-04-12 195411" src="https://github.com/user-attachments/assets/f470ff9f-074d-484c-978b-d797f6c40d24" />

<img width="439" height="326" alt="Screenshot 2025-04-23 203002" src="https://github.com/user-attachments/assets/7da2c3fa-6b09-4e81-95d0-6c40f62dedea" />

Using raster calculator operations, I integrated the feature heights with the elevation model to produce a Digital Surface Model (DSM). This allowed both terrain and above-ground features (buildings, vegetation, infrastructure) to be represented in a single surface.

<img width="227" height="318" alt="Screenshot 2025-04-12 200317" src="https://github.com/user-attachments/assets/d2258fb0-5f05-4a04-bc7e-874df1822708" />

<img width="415" height="384" alt="Screenshot 2025-04-23 202901" src="https://github.com/user-attachments/assets/30b620ac-2268-4614-b75f-abcdb082594f" />

Then I added my new file to the DEM to produce my DSM.

<img width="232" height="302" alt="Screenshot 2025-04-12 200500" src="https://github.com/user-attachments/assets/85255a14-e306-4fc6-94a7-579ccef76563" />

<img width="469" height="380" alt="Screenshot 2025-04-12 201450" src="https://github.com/user-attachments/assets/f6a575d8-76a2-4510-875f-1290366c9a69" />

## 3D Output & Physical Model

The DSM was exported and brought into QGIS to generate a file compatible with a 3D printer.

This step extended the project beyond visualization and into physical modeling, producing a tangible representation of the farm’s landscape and structures.

<img width="333" height="371" alt="Screenshot 2025-04-20 190236" src="https://github.com/user-attachments/assets/fc423f6d-2607-4956-b637-81bdf6ca9f98" />

<img width="362" height="494" alt="Screenshot 2025-04-23 202134" src="https://github.com/user-attachments/assets/22845027-7abe-4ac4-a4f1-b00b9b0bb5a9" />

## Final result:

The final output was a 3D-rendered model of the farm that captures both elevation and structural features. This type of model can be useful for site planning, visualization, and understanding how built and natural environments interact spatially.

<img width="560" height="307" alt="Screenshot 2025-04-23 202244" src="https://github.com/user-attachments/assets/005765fd-9119-449d-acc7-b6a0c835df46" />

## Limitations & Future Improvements

- Building heights were manually estimated rather than derived from LiDAR or precise measurements
- Tree and vegetation heights were generalized rather than species-specific
- Roof structures were simplified due to limitations of the available 3D printing setup

In future iterations, I would explore incorporating more accurate elevation and structural data, as well as improving roof geometry to better reflect real-world conditions.

