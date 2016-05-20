# db_data

## Description of Data

This corpus contains the overlapping data from the [Million Song Dataset (MSD)](http://labrosa.ee.columbia.edu/millionsong/), [musiXmatch dataset](http://labrosa.ee.columbia.edu/millionsong/musixmatch), and [Tagtraum datasets](http://www.tagtraum.com/msd_genre_datasets.html). In order to achieve this we identified track IDs that existed in all three. This left a dataset size of roughly 1200 songs. The overall goal was to provide a dataset that was database independent so everyone can easily access this subset. 

otherdata.csv: Information from Tagtraum and MXM. Note genre field may contain two values. | symbol separates genres and words. detailed Headers: track_id, genre|genre, word|count

subset/: Information from MSD. Includes song data information such as artist name, song name, ect.  

common_songs.txt: Track IDs that intersect between MXM and Tagtraum datasets. 

msd_tagtraum_cd2.cls: Tagtraum data

geo-information.csv: Geography data from subset

- otherdata.csv: Information from Tagtraum and MXM.
- subset/: Information from MSD
- common_songs.txt: Overlap between MXM and Tagtraum datasets
- msd_tagtraum_cd2.cls: Tagtraum data
- geo-information.csv: Geography data from subset


## Scripts

extract_data.py: Python script that extracts the overlapping data between MSD, MXM, and Tagtraum datasets. This is how the csv was generated. Task: Read in data from the datasets, find the intersecting data, convert data into csv format.

extract_geography_data.py: extracts track_id, artist_location, artist_latitude, artist_longitude from all h5 files of subset. The result file is geo-information.csv. You need "subset" and "PythonSrc" folder as a subfolder for the execution.

## Arguments:
	Note: Path information will need to be changed. Examples provided below. 
	- msd: Path to MillionSongSubset or MillionSongDataset folders. Ex: '/home/usr/path/to/dir/MillionSongSubset'
	- msdtoolkit: Path to MSongsDB folder. This is a toolkit that can be downloaded from the MillionSongDataset website. Ex: '/home/usr/path/to/dir/MSongsDB' 
	- tagtraum: Path to Tagtraum dataset (msd_tagtraum_cd2.cls)
	- mxm: Path to MXM dataset (mxm_dataset.db) '/home/usr/path/to/dir/MillionSongSubset/mxm_dataset.db'

## Executing the script:
To run the extract_data.py script, you need to have python3 installed on your machine. Information on getting python3 can be found [here](https://www.python.org/downloads/). In Python 2.7 the csv file will be incorrectly generated due to unicode formatting behavior. Formatting the detailed information in the MSD in csv format is not realistic due to the sheer size of the subset. To extract that data, see [here](http://labrosa.ee.columbia.edu/millionsong/pages/basic-getters-functions).
        
Type this command in a terminal window: `python3 extract_data.py`

