# Inference of Technical Data from CCTV images

The submitted workflow is written using Python 3 and performs object detection of people on videos. It takes videos as inputs and outputs predictions in the shape of a table (dataframe) on Dataiku. Those outputs are used to plot a number of people vs time, necessary for analysis (described in detail in the report).

As this project involves the use of confidential data (videos) from Schlumberger, the training dataset and the videos processed won't be inserted in this repository.
Also, as it doesn't seem possible to upload it here, a .pt file was created after training and it is not present on this repo.

## Contents
### cctv-ml-workflow folder
#### Useful .py files
* bbox_util.py: useful functions for data augmentation in object detection
* coco_eval.py and coco_utils.py: functions used in engine.py 
* utils.py: useful functions
* engine.py: train and evaluate functions for object detection

#### Main files
* custom_dataset.py: CustomImageTensorDataset class, written to apply transforms to both "img" and "target" (boxes). 
* data_augmentation.py: Custom transforms for data augmentation in object detection.
* ml.py: Main code for training. Uses all the previously mentioned files to train a model.
* compute_toto.py: Main code to perform predictions using a trained model on videos available on Dataiku. Used on Dataiku (https://www.dataiku.com/ for more information about the data platform).
* yt-loading-and-predicting.ipynb: Gets the results of prediction for public data downloaded from Youtube. Can plot the corresponding frame and its predicted boxes (detected people). 

#### For data preparation
Videos_to_images.ipynb: Extract frames from videos every per_frame frames and saves them as .jpg images. 

#### Analysis of results
people-vs-time_plot.ipynb: From predictions, plots the number of people detected vs time (i.e. at which time they were detected).

### Report
final-report_Laura-Su.pdf: This report gives a detailed description of the steps taken and the analysis done.

## Requirements
### System
Windows or Linux

### Software (optional)
LabelImg software to get from https://github.com/tzutalin/labelImg

### Packages
#### opencv
```pip install opencv-python```

#### pytorch (with or without CUDA)
Follow the instructions on https://pytorch.org/

#### pycocotools
##### Windows
Follow the instructions on https://github.com/philferriere/cocoapi

##### Linux
Get the repository from https://github.com/cocodataset/cocoapi

## Usage
With this repository, as the dataset and the .pt file are lacking, it won't be possible to run the code. Please contact me (lcs18@ic.ac.uk) if you want to get the .pt file to run the predictions.

Using Pycharm and Jupyter Notebook is recommended.
This repository can be downloaded on your computer. All required packages must be installed.

The optional software is for labelling, if desired.

Once all the files are retrieved, open Jupyter Notebook and run yt-loading-and-predicting.ipynb (choose a proper Youtube video involving roughnecks working on a rig) to have a first visualisation of possible results.


## Built with
Python 3

## Author
Laura Su (lcs18@ic.ac.uk)

## Acknowledgments
* Dr Robert Zimmerman (Imperial College London), Adam Bowler and David Halliday (Schlumberger), my supervisors for their support
* Schlumberger for accepting me for an internship
* Family, friends and fellow interns for their moral support

## License
This project is licensed under the MIT license - check LICENSE file for more details.
