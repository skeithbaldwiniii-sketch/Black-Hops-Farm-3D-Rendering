# Black-Hops-Farm-3D-Rendering
## 3D Farm Modeling & DSM Creation (Loudoun County, VA)
Integrated multi-source geospatial datasets and executed raster/vector workflows (merge, buffer, raster calculator) in ArcGIS Pro to generate a Digital Surface Model for 3D landscape visualization 

This was my final project in the GIS 3-Dimensional Analysis course at Northern Virginia Community College, which I completed in May 2025. The end goal was to create a 3D model of the farm where I was employed when I completed the course. 

Like most of my projects, I started with the Loudoun GeoHub to see what map layers were publicly available. These were the parcels, buildings, forest, trees, water bodies, and road casing shapfiles. I used a combination of "create layer from selection" for the parcel, and clip features to isolate the details from each layer that I need. 

<img width="1117" height="604" alt="Screenshot 2025-04-12 173855" src="https://github.com/user-attachments/assets/377ffca3-5f28-4bed-aedc-70b1da9d0fb4" />

I also retrieved the DEM from Earth Explorer to save for a later step. 

I manually inputted the height of the low end of each roof in meters by adding a field on the buildings layer and then modifying the value. One building in particular needed to be separated because different sections were different heights, so I used the split polygon tool to make those divisions. 

<img width="999" height="530" alt="Screenshot 2025-04-12 180628" src="https://github.com/user-attachments/assets/01cdd4be-5ebe-405a-8b75-72916a36b744" />

I then used the raster calculator to edit the attribute table on the trees layer to make them all a height of 8 m, the forest layer to 1 m, and the pond and roads layer to 0.5 m so they can show some definition when being rendered

<img width="470" height="539" alt="Screenshot 2025-04-12 193136" src="https://github.com/user-attachments/assets/dc34d2a3-0be2-4181-ae1f-811408944a5a" />

I ran the merge geoprocession tool to combine the road, forest, buildings, and water layers so I can process them all together instead of separately. The merge tool only works with similar feature types, points OR polygons, so I needed to convert my trees dataset so they would be compatible. For this, I ran pairwise buffer. Then added their height in the attribute table, making them 8 m. Then I merged all of the polygons. 

<img width="391" height="452" alt="Screenshot 2025-04-16 223151" src="https://github.com/user-attachments/assets/5f89586d-8e81-4e22-b9a5-bf4831fd533d" />

<img width="386" height="487" alt="Screenshot 2025-04-12 191959" src="https://github.com/user-attachments/assets/78012d82-af1b-42be-932e-2bf973e21364" />

<img width="693" height="585" alt="Screenshot 2025-04-23 202820" src="https://github.com/user-attachments/assets/caa5df3c-62c0-4c22-af75-20ec9a837f93" />

I then ran the feature to raster tool so the merged polygon file could be used for raster processing. 

<img width="395" height="390" alt="Screenshot 2025-04-12 195411" src="https://github.com/user-attachments/assets/f470ff9f-074d-484c-978b-d797f6c40d24" />

<img width="895" height="666" alt="Screenshot 2025-04-23 203002" src="https://github.com/user-attachments/assets/7da2c3fa-6b09-4e81-95d0-6c40f62dedea" />

I then ran the raster calculator. 

<img width="386" height="540" alt="Screenshot 2025-04-12 200317" src="https://github.com/user-attachments/assets/d2258fb0-5f05-4a04-bc7e-874df1822708" />

<img width="706" height="653" alt="Screenshot 2025-04-23 202901" src="https://github.com/user-attachments/assets/30b620ac-2268-4614-b75f-abcdb082594f" />

Then I added my new file to the DEM to produce my DSM.

<img width="393" height="514" alt="Screenshot 2025-04-12 200500" src="https://github.com/user-attachments/assets/85255a14-e306-4fc6-94a7-579ccef76563" />

<img width="798" height="647" alt="Screenshot 2025-04-12 201450" src="https://github.com/user-attachments/assets/f6a575d8-76a2-4510-875f-1290366c9a69" />

This DSM I then exported so I can plug into QGIS to produce the file compatible for the 3d printer. 

<img width="680" height="757" alt="Screenshot 2025-04-20 190236" src="https://github.com/user-attachments/assets/fc423f6d-2607-4956-b637-81bdf6ca9f98" />

<img width="617" height="840" alt="Screenshot 2025-04-23 202134" src="https://github.com/user-attachments/assets/22845027-7abe-4ac4-a4f1-b00b9b0bb5a9" />

Final result:

<img width="1143" height="626" alt="Screenshot 2025-04-23 202244" src="https://github.com/user-attachments/assets/005765fd-9119-449d-acc7-b6a0c835df46" />

For a future iteration, I would like to explore how I could make the roof shaped to be more accurate to the property. With the 3D printer I was limited to, this was not possible, but in a much more advanced 3D printer it could be something worth exploring. 

