# cloud_assignment1
### URK18CS226
## _Stream your data to the cloud and visualise your data dynamically using chart.js_
### Cloud service used: ```Google Cloud```
## 1. Creating project
* A google cloud platform project is needed. If you don't have one follow the steps to create it.
* In the navigation menu, select _IAM & Admin -> Manage resources_.
* Click on _Create Project_.
* Give your desired project name. Project name should be unique.
* If your mail-id is a part of an organization, your organization will be displayed. You can switch to No organization if you don't want your organization name.
* If your mail-id is personal, it will be set to No organization by default.
* Click on _Create_ after giving the needed details.

## 2. Visualization JS file
* Create a folder in your system to save all the files to be created in the upcoming steps.
* Click on dscc.min.js in [Data Studio Community Component Library](https://developers.google.com/datastudio/visualization/library) and copy the contents in the file and save it your local system in a notepad as a JavaScript file with name ```dscc.min.js```.
* Copy the [code](https://github.com/rachelbdavid/cloud_assignment1/blob/main/code/chartSource.js) into a notepad and name it as ```chartSource.js``` in your local system.
* Combine all the JavaScript files by concatenating _dscc.min.js_ and _chartSource.js_.
* In the command prompt, go to the file location where the JavaScript files are saved.
* Use the following commands to concatenate _dscc.min.js_ and _chartSource.js_.
```
del chart.js
type nul > chart.js
type dscc.min.js >> chart.js
echo.>> chart.js
type chartSource.js >> chart.js

```
## 3. Visualization CSS file
* In the same folder where the JavaScript files are stored, copy the CSS [code](https://github.com/rachelbdavid/cloud_assignment1/blob/main/code/chart.css) and save it in a notepad with name ```chart.css```.
* CSS file is for styling of the visualization.

## 4.JSON config file
* The visualization config json file defines the data and style attributes supported and required by your visualization.
* Copy the [code](https://github.com/rachelbdavid/cloud_assignment1/blob/main/code/chart.json) and save it in your notepad with name ```chart.json```.

## 5. Creating bucket
* In the navigation menu, go to _Cloud Storage -> Browser_.
* Click on _Create Bucket_ on top of the console.
* For bucket name, give a unique name (here [cs226_assignment1](https://github.com/rachelbdavid/cloud_assignment1/blob/main/IMG/bucket.JPG)) and click _Continue_.
* For Choose where to store your data option, select _Region_ and click Continue.
*	For Choose a default storage class for your data option, select _Standard_ and click Continue.
*	Leave other values as default and click on _Create_ button.
*	After bucket is created, the console will show the details of the bucket.
*	Click on _Create folder_ option and give the folder name as ```chart```.
*	Click on that folder name. You’ll be inside the created folder.
*	Copy the path of the bucket by clicking on the copy icon.

## 6. Uploading files to cloud bucket
* In the cloud bucket, inside chart folder, click on _Upload files_.
* Select chart.js, chart.css, chart.json and manifest.json to upload to bucket.
* After uploading, we should change the access of each file uploaded.
* Click on the three-dots at the end of the file name.
* Choose _Edit permissions_ from the options.
* In the pop-up window, click on _Add entry_.
* Select _Entity_ as ```Public```, _Name_ as ```allUsers``` and _Access_ as ```Reader```.
* After giving these values, click _Save_.
* After repeating the process for all the four files, the details of all the files should be similar to this [figure](https://github.com/rachelbdavid/cloud_assignment1/blob/main/samples/files.jpg).

## 7. Creating manifest.json file
* Copy the [code](https://github.com/rachelbdavid/cloud_assignment1/blob/main/code/manifest.json) and paste it in a notepad.
* In the resource section of the code, for js, css, and config, add the bucket path of chart.js, chart.css and chart.json.
```
"resource": {
      "js": "gs://cs226_assignment1/chart/chart.js",
      "config": "gs://cs226_assignment1/chart/chart.json",
      "css": "gs://cs226_assignment1/chart/chart.css"
    }
```
* Save this file with name ```manifest.json```.

## 8. Testing the visualization in Data Studio
*	Copy this [sample dataset link](https://docs.google.com/spreadsheets/d/1LVtnNRXAQxjhzZUPagyBfaV6PywrL9Xs-gs-FZzQLxE/edit#gid=0) for testing the visualization code.
*	Go to [Data Studio](http://datastudio.google.com/) and create a blank report.
*	Click on Google sheets in _add data to report_ under _connect to data_ tab. [(Sample image)](https://github.com/rachelbdavid/cloud_assignment1/blob/main/samples/add_data.jpg)
*	Select _URL_ from the left menu and paste the sample dataset link.
*	Click on _Add_ to create the report.
*	In the right hand panel, set _Dimension_ to ```Age Grop```, _Metric_ and _Sort_ to ```Population```. 
*	The values can be changed by clicking on the value box and choosing the desired parwameter from the pop-up menu.
*	In the taskbar, click on [Community visualization button](https://github.com/rachelbdavid/cloud_assignment1/blob/main/samples/plot.jpg) and click _+Explore more_.
*	In the options shown, choose _Build your own visualization_.
*	Give the cloud bucket folder path in the [_Manifest path_](https://github.com/rachelbdavid/cloud_assignment1/blob/main/samples/linking.jpg). The path should be in format ```gs://cs226_assignment1/chart```.
*	Click on _Submit_.
*	A _bar chart_ option will be shown below the bucket path.
*	Click on _bar chart_ and click on the main chart window to place the bar chart in the report.
*	Now the [output chart](https://github.com/rachelbdavid/cloud_assignment1/blob/main/IMG/output.JPG) created by the use of _chart.js_ and _chart.css_ will be displayed in the report. 
