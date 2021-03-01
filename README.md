Provisional repository for manual and developments of D+Flow Slide batch tool

# D-Flow Slide Batch tool

Batch Tool Interface for D-Flow Slides. The interface also takes care of input preparation and generation for D-Flow Slide computation.

*D-Flow Slide - background [here](https://publicwiki.deltares.nl/display/GEO/Background+-+Detailed+check)* 

*Batch tool repository [here](https://repos.deltares.nl/repos/DFS)* 

---

## Interface
The interface main window shows the general options the user can select. With `Input files` the user can select the input file to be ingested in D-Flow Slide. The button `Folder D-Flow Slide` let the user select the folder where the kernel of D-Flow Slide is in. The computation will make use of the libraries and executables contained in that folder. With `Folder Results`, the user selects the output folder for the run. Once the information from these three buttons is gathered, the `Run` button will activate and run D-Flow Slide. The user can either start another run with other input values or exit the interface by pressing `Exit`. Keep in mind that a log of the computation is shown in the terminal, so that the user always knows what is happening under the hood. 

![win_main](static/win_main.jpeg)

---

Pressing `Input Files` let the user decide whether the input is simply selected or it is generated. The choice is presented between three different ways of generating the excel input files for D-Flow Slide run. If input excel files are already in place, select the button `Excel files`. This opens a window for direct selection of the input folder. The other two options allow for the generation of the input. With the first button `Extract` the user can generate the input files from a shapefile containing transects and a number of rasters of bathymetry and topography. The button `Morphan` let the user generate input files directly from Morphan output files. The latter workflow is still *in progress*. 

![win_selectinput.jpeg](static/win_selectinput.jpeg)

---

Pressing `Extract` opens a menu for the extraction of input files from bathymetry/topography and shapefile. The user select the location of .tif bathymetric files by clicking on `Input rasters`. The location of topographic files is given by clicking on `Input ahn`. A shapefile containing cross-shore transects is selected with `Input shapefile`. The shapefile can contain one or multiple shapefiles. The button `Output extraction` let the user select the location of the output of this raster extraction analysis. Once the above mentioned options are determined, the button `Run extraction` will execute the extraction code. This may take a minute, however the output from terminal shows the running tasks. The next operations aim at finding characteristic points and writing the excel file to use as input of D-Flow Slide. Once the profiles have been extracted from rasters, next time the user opens the interface, the user can directly start from these last remaining steps, so that the extraction does not have to take place every time the interface is opened. Click on `Select profiles` to select just a number of profiles from the ones extracted in the previous steps. Click `Find points` to find characteristic points from the selected profiles. The windows that pop-up will also ask for a kering shapefile to easily determine the side of the river/channel to calculate the characteristic points from. This may take a minute, so wait for the bar to finish and follow the operations from the terminal. The button `Write excel` writes excel in a folder the user chooses. `Save and Return` will return to the main interface window. 

![win_inputfromraster.jpeg](static/win_inputfromraster.jpeg)

NB: All the windows that pop-up have a title explaining what the user should do. This helps a lot to direct actions.

---


## Getting started
A tutorial is presented here.

### Run on existing input files

### Extract profiles from raster

### Find characteristic points and generate input file for DFlowSlide
Once the rester extraction is done, the next commands can be executed.

NB. If the extraction of raster has been already carried out, there is no need to follow the entire procedure from the beginning. In fact, once the rasters are interpolated along the cross transects, profiles are obtained and saved in the "raw" folder. At this point, the characteristic points and the DFlowSlide excel input files can be obtained, without processing any raster. 

### Extract profiles from Morphan
In progress.

### Run DFlowSlide batch tool


---

## Prerequisites

Anaconda3 and python 3.7 is used through the development of the input generation for the batch tool
The stand-alone configuration of the batch tool let the user avoid the set-up of an environment or an environment.yml file, 

---

## Authors
* **Giorgio Santinelli**
* **Maria Luisa Taccari**
* **Bruno Zuada Coelho**

