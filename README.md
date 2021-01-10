# dflowslide_batchtool
Provisional repository for manual and developments of DFlow-Slide batch tool

# D-Flow Slide Inputs creation

Batch Tool Interface for D-Flow Slides. The interface also takes care of input preparation and generation D-Flow Slides

*D-Flow Slide - background [here](https://publicwiki.deltares.nl/display/GEO/Background+-+Detailed+check)* 

*Batch tool repository [here](https://repos.deltares.nl/repos/DFS)* 

---

## Interface


![win_main](static/win_main.jpeg)

---

![win_selectinput.jpeg](static/win_selectinput.jpeg)

---

![win_inputfromraster.jpeg](static/win_inputfromraster.jpeg)

---


## Getting started

### Input files
When clicking on **Input files** button, another window open where the choice is presented between three different ways of generating the excel input files for D-Flow Slide run. 


### Folder DFlowSlides  


### Folder results

### Exit
The **Exit** button closes the main window. 

Downloading the Digital Elevation Model data for the area of interest:  
* Define boundingbox of area of interest (File "clip_ahn.py", line 83)
* Run clip_ahn.py in cmd
* Enter local path to gdal_merge (File "clip_ahn.py", line 83)  

Create input folders containing: 

1.	Topographic data of the river (*.tif)
2.	Longitudinal section of the dike (*.shp)
3.	Cross sections of the dike (*.shp) 

Provide the local paths in the .py scripts whenever a local path is required. 
Read and merge the topographic data of the river with the Digital Elevation Model data for each cross section of the dike: 

```
raster_extract.py
```
### Define the characteristic points
Definition of characteristic points *Dike Top*, *Bottom River Channel*, *Insert river channel*
and *Dike Toe*.  
```
Run characteristic_points.py in cmd

Are you satisfied with the characteristic points automatically chosen? If not, select them manually.
```

You can read how characteristic points are used in the detailed check in the [schematiseringshandleiding](https://publicwiki.deltares.nl/download/attachments/90409971/1220078-007-GEO-0007-v3-r-Schematiseringshandleiding%20zettingsvloeiing_v3revised_final.pdf?version=1&modificationDate=1445427580000&api=v2)

### Create input files for Batch Tool 
Creation of Excel files (*.xlsx) for the Batch Tool. 

```
write_excel.py 
```

Use the created excel files as inputs for the Batch Tool.

---

## Prerequisites

Anaconda3 and python 3.7 is used through the development of the input generation for the batch tool
The stand-alone configuration of the batch tool let the user avoid the set-up of an environment or an environment.yml file, 

Use the terminal or an Anaconda Prompt for the following steps:

---

## Authors
* **Giorgio Santinelli**
* **Maria Luisa Taccari**

