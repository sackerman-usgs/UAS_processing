# UAS_processing
Creators: Seth Ackerman (@sackerman-usgs), Emily Sturdivant (@esturdivant-usgs), Chris Sherwood (@csherwood-usgs)

Jupyter notebook to process image and GPX files.


## Detailed workflow:

1. read the GPX file, which is a telemetry log file produced by the 3DR Solo in tlog format and converted to GPX in Mission Planner. View a dataframe from the GPX file.
2. Parse the time field in the GPX dataframe. Add fields datetime_utc and epoch_utc.
3. Export the dataframe as a table in CSV format and make a basic map of the flight path from the GPX navigation data.
4. Plot the flight path on an aerial photo basemap.
5. Initialize an dataframe for the images. Include the original filename and the time in UTC, Epoch, and ISO formats.
6. Export a CSV of the dataframe. Plot the image times and the GPX elevations by time to check that they match.
7. Rename the photos using the survey number, the flight and camera ID, the time in ISO format, and the original filename.
8. Geotag the photos from the GPX file using the Geosync tool in ExifTool.
9. Update the EXIF tags to standard values.

## Requirements
Python 3 with modules (in addition to defaults):

- lxml
- PIL, which includes ExifTool by Phil Harvey
- pandas
- numpy
- matplotlib

These are satisfied by using the `IOOS3` environment in Anaconda.


## Instructions

input variables:

- homedir: working directory that contains image folder and tlog folder (with gpx file) and where outputs will be saved.
- flight: flight ID that matches the image folder name and the gpx file, usually in format fX

created variables:

- logfile: gpx file path
- imagefolder: image folder path

output products:

- CSV of pertinent telemetry data converted from GPX
- PNG of flight path created from GPX
- new folder of images with standardized filenames and image headers populated with contextual information


### To use ipyleaflet

```
conda install -c conda-forge ipyleaflet
```


```
pip install ipyleaflet
jupyter nbextension enable --py --sys-prefix ipyleaflet
```
