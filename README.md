# ORB-SLAM3-Datasets-Preprocessing
* At first you need to preprocess the dataset. Preprocessing includes the transformation of depth images into RGB images coordinates and converting pictures to undistorted format. You can do this by executing:
```
python preprocessing.py DEPTH_MASTER_IMAGES COLOR_MASTER_IMAGES DEPTH_SLAVE_IMAGES COLOR_SLAVE_IMAGES INI_CONFIG_FILE
```
**WARNING**: You should have requirements installed for running script.

*NOTE*: You should specify config.ini file before running script. There is example of this file in the repository.

Your preproccesed files will be in ```depth_master_preprocessed```, ```color_master_preprocessed```, ```depth_slave_preprocessed```, ```color_slave_preprocessed``` folders.

* Then you can generate your own associations file executing:
```
python associate.py PATH_TO_RGB_MASTER PATH_TO_DEPTH_MASTER PATH_TO_RGB_SLAVE PATH_TO_DEPTH_SLAVE > associations.txt
```

*NOTE*: You can specify max_difference and timestamp2sec parameters. By default they equals 1000 microseconds and 1e6 accordingly.

* Now you can run ORB-SLAM3:
```
./Examples/RGB-D/rgbd_tum Vocabulary/ORBvoc.txt SETTINGS_YAML_FILE PATH_TO_SEQUENCE_FOLDER ASSOCIATIONS_FILE
```
*NOTE*: The repository already has a yaml configuration file for `multi_azure_recorded_circle` dataset.