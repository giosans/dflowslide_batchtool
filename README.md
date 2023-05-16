
# DFlowSlide Batch Tool manual
The Batch Tool DFlowSlide has undergone many changes in the last 3 years. In 2022, the code has been refactored and cleaned to enable easier development, improve modularity, deployment, and user-readability. The Batch Tool consists of an interface that takes care of the input reading and pre-processing, and the running for DFlowSlide computations.

A little background on D-FlowSlide is available from the wiki-page:
*D-Flow Slide - background [here](https://publicwiki.deltares.nl/display/GEO/Background+-+Detailed+check)* 

The repository is on Github, available *[here](https://github.com/Deltares/DFlowSlide_batchtool)* 

---

## Getting started
The tool can work on Windows platforms, and it is an executable called `D-FlowSlide_Batchtool.exe`. After clicking on the executable, wait half a minute for the application to start. Once started, the application will look like the following.

![win_main](static/landing_page.png)

### Requirements
Running the D-Flow Slide Batch tool requires:
* raster ('tif') bathymetric file or files;
* raster ('tif') topographic file or files;
* cross river transects ('shp') along which we interpolate the rasters and obtain the profiles;
* barrier line ('shp') shapefile of a line which represents the keringlijn, to help determining what side is the profile to be tested and hence the transect/profile direction.

### Technical Requirements
Requirements and environment file for local installation and testing are maintained on [this repository](https://github.com/Deltares/DFlowSlide_batchtool).
The stand-alone configuration (.exe) of the batch tool has the advantage of being built with modern development CI/CD workflows, with unit and acceptance testing, and ultimately to keep the user free from local building from code. 

---
## Tutorial
The interface main window shows the general options the user can select. The `Select Source` cascading menu lets you choose between running D-FlowSlide calculation with the processed .xls input files of D-FlowSlide, or generate those input files through a process of extraction of transects and characteristic points detection. To run with .xls insput files, choose the option `Excel files` in the `Select Source` menu. To generate the input files through extraction and characteristic points, select `Extract files`. These options will be discussed in the following two sections.

### Run D-Flow Slide with input excel files
Once you select `Excel files` in the `Select Source` option, you can proceed with filling in the other fields. With `DFlowSlide Version` the user selects the binary folder where the kernel of D-Flow Slide is in. The computation will make use of the libraries and executables contained in that folder. If the user has already processed .xls input files of D-FlowSlide, the user selects the output folder for the D-Flowslide run with `Results directory`. Once these fields are filled in, the `Run calculation` button will activate and run D-FlowSlide. The user can either start another run with other input values or exit the interface by closing the tool. 

![win_main](static/excel_results_action.png)

### Extract files, find points and run D-Flow Slide
Once the `Extract files` option is selected in the `Select Source` menu, the user can fill in all fields for extraction of profiles from rasters, finding characteristic points and writing excel input files for DFlowSlide. This is what the extraction window looks like.

![win_main](static/extract_general.png)


The `Extract data` tab shows the fields. Once they are all filled in, the `Run extraction` button is activated, and can be started to start the extraction. Once all the data is extracted, the `Select transects` tab lets the user select the proper transects from the extraction folder, which is inside the `raw` folder. At this point the `Characteristic Points` tab can be opened. There the `kering shapefile` field should be inserted. If done properly, the  `Find Points` button should be activated. 
If the `calculation mode` is selected as `Auto`, then finding the points will happen in an automated way. If the mode is `Manual` the plots per profile will be open and the user will go through each of those plots and follow the instructions given in the image. Here is an example of plot; the instructions for the user are shwon in the plot title.

![win_main](static/choose_method.png)

![win_main](static/findpoints_auto.png)

![win_main](static/findpoints_manual.png)


Either way, when you read "Characteristic points computed" in the logging, you can go to the next step. The button `Export to .xlsx` writes the input excels for D-FlowSlide. After that, the `Run calculation` button will activate and by clicking it D-FlowSlide will run. 

--- 

## Other options of usage
### Import and export .dbt files
By clicking on `File` from cascading menu, three options open that interact with a settings .json file with `.dbt` extension. The three options let you: 
* New: Swip out all changes, and start with a new clean interface;
* Export: This will create a new `.dbt` file to which a name can be given; 
* Import: If you already have a previously exported `.dbt` file, you can simply import it here. Doing so will automatically fill in the fields from the interface. 

### Rerun the tool with different files
If you would like to keep the same settings but just need changing files, you can import a previously exported `.dbt` file and just import the path of those new files from the interface. This tip is valid for any setting you may want to change.

### Re-run auto detection as manual
If after the auto detection the user is not satisfied, importing the `.dbt` file will help to restore all settings and just find points in a manual way.

---

## Description of the tool tabs and buttons

The tool consists of an `Action` panel with buttons, a tabs panel for selection of input, and a `Status Panel` with logging showing the status of the selection and calculation. 
The `General` tab let the user decide whether the input is simply selected or it is generated. If Excel option is chosen, the tab `Excel input` guides the user in the selection of the input files, and the `Run calculation` button is activated. The `Extract files` option allow for the generation of the input for D-FlowSlide. By selecting it as source, new tabs and buttons are generated in the interface so the user can generate the input files for D-FlowSlide from a shapefile containing transects and a number of rasters of bathymetry and topography. 
When running with `Extract files` mode, the `General` tab does not change. The tabs `Extract data`, `Select Transects`, `Characteristic Points` and the new buttons `Run extraction`, `Find Points`, `Export to .xlsx` appear. `Raster Folder` asks for a folder with raster files, namely bathymetric surveys. `AHN File` asks for a single topographic file for integration of the surveys. A shapefile containing cross-shore transects is selected with `Cross-section (*.shp)`. The shapefile can contain one or multiple shapefiles. The field `Extraction output folder` let the user select the location of the output of this raster extraction analysis. Now the button `Run extraction` is enabled. The following tab `Select transects` let you select the transect once the `Run extraction` analysis is complete. Alternatively, you can still select the folder where transects previously computed are stored. The tab `Characteristic Points` let the user select an along-section kering shapefile and select the calculation mode from the  `Calculation mode` menu. Once all fields  are complete, the two buttons `Find points` and `Export to .xlsx` perform finding characteristic points and writing the excel file to use as input of D-FlowSlide, respectively. `Run calculation` can be run to let D-FlowSlide compute on the input files and the settings given.

NB: All the windows that pop-up have a title explaining what the user should do. This helps to direct actions throughout the process.

---

### Further developments
Pending development actions to the tool are not available at the moment and comprise:
- Insert multiple soil layers
- Better definition of top revetment and bottom revetment
- Choosing auto / manual selection of characteristic points after each profile
- Extracting profiles from Morphan
- Rebuild as a browser application

---

---

## Authors
* **Giorgio Santinelli**
* **Carles Soriano Perez**
* **Maria Luisa Taccari**
* **Bruno Zuada Coelho**

