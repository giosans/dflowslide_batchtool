Provisional repository for manual and developments of D+Flow Slide batch tool

# D-Flow Slide Inputs creation

Batch Tool Interface for D-Flow Slides. The interface also takes care of input preparation and generation for D-Flow Slide computation.

*D-Flow Slide - background [here](https://publicwiki.deltares.nl/display/GEO/Background+-+Detailed+check)* 

*Batch tool repository [here](https://repos.deltares.nl/repos/DFS)* 

---

## Interface
The interface main window shows the general options the user can select. With `Input files` the user can select the input file to be ingested in D-Flow Slide. The button `Folder D-Flow Slide` let the user select the folder where the kernel of D-Flow Slide is in. The computation will make use of the libraries and executables contained in that folder. With `Folder Results`, the user selects the output folder for the run. Once the information from these three buttons is gathered, the `Run` button will activate and run D-Flow Slide. The user can either start another run with other input values or exit the interface by pressing `Exit`. Keep in mind that a log of the computation is shown in the terminal, so that the user always knows what is happening under the hood. 

![win_main](static/win_main.jpeg)

---

Pressing `Input Files` let the user decide whether the input is simply selected or it is generated. If input excel files are already in place, select the button `Excel files`. This opens a window for direct selection of the input folder. The other two options allow for the generation of the input. With the first button `Extract` the user can generate the input files from a shapefile containing transects and a number of rasters of bathymetry and topography. The button `Morphan` let the user generate input files directly from Morphan output files. The latter workflow is still *in progress*. 

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

