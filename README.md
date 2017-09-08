# MSL Datamining Script
This script performs the action of converting MODRDR data from the MSL dataset into a csv format for insertion into XINA.

## Setup
The directory contains two necessary files:
 - properties.json
 - write.<i></i>py

#### properties.json
The properties defines the write location of the CSV/JSON files and also defines the read location of the MSL dataset.

Edit the `write_location: ""` and `data_path: ""` entries with the desired path.

Example:
`write_location: "./CONVERTED_DATA/"`
`data_path: "./RAW_DATA/SOL_1-50/"`

It is important to note that the write location must already exist and must also have a directory named `CSV` within it for the script to generate the files correctly.

#### write.<i></i>py
Executing this script will read the properties.json file and begin the mining process.

It will proceed to traverse the directory defined in `data_path` and record the paths to each file containing `RMD` in the file name and `TAB` as the extension. These files hold the MODRDR data, which is the data post-processing and adjustment.

The script will then access each file according to the recorded path and create a CSV file. It will write the first row that contains the column names.

Next, each file is read line by line and each line is formatted to remove un-wanted data. The time stamps are converted to the appropriate format and added to the line before it is added to the file.

Lastly, the script creates a JSON file using the filepath to the CSV as it's object id.

## Usage

`$ python write.py`

or

```
$ chmod +x write.py
$ ./write.py
```
