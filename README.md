

# How to load data from PHE Fingertips Website into NQM TDX

## Getting Started

 
Download [python 3 via anaconda](https://www.continuum.io/downloads)

and [node](https://nodejs.org/en/download/)


clone this folder to a local repository

git clone https://github.com/lv1903/PHE_Fingertips_Import.git


and then install the nqm json importer

in the command line enter

npm nqm-json-import




## Import Steps

**1)** Set up a PHE download config json file

eg config_PHE_fingertips_lape_DU.json

-->

{
    "url": "http://livews-a.phe.org.uk/GetDataDownload.ashx?pid=87&ati=101&res=87&tem=87&par=E92000001&pds=0&pat=6", 
    "sheet": "District & UA", 
    "output_path": "C:/dev/PHE_Fingertips_Import_Process/", 
	"output_filename": "output.json",
    "required_indicators": [],
	"profile": "Local Alcohol Profiles for England",
	"download_version": ""
}

You need to find the url for the xls download.
The url is hidden, you have inspect the browser console from the download page for the path
(The url usually does not change when they update the data.)


And find out what sheet the data is on.


Leave required_indicators array blank if you want all indicators


**2)** then in the command line run
python PHE_fingertips_downloader.py --config <config name>.json


**3)** and finally

node ./node_modules/nqm-json-import/nqm-json-import --sourceFile output.json --config nqm-json-import-config.js


if there is a proble with the nqm-json-import

you can debug the import process

in the command line type

set debug=*

and re-run the import















