# Machine Learning Engineer Nanodegree Capstone Project

## Understanding the Amazon from Space


### Overview

The goal of this project is to track changes in the Amazon rainforest due to deforestation using satellite image data. It is a multi-label image classification problem introduced in a past Kaggle competition [Planet: Understanding the Amazon from Space](https://www.kaggle.com/c/planet-understanding-the-amazon-from-space). The final solution consists of an ensemble of five deep learning models using transfer learning with the fastai library which would have placed 19th in the competition. 

You can read my full project report [here](./report.pdf)

You can see my original project proposal [here](./proposal.pdf)


### Requirements

To run the notebooks you can create a conda environment with all necessary software by running:

```conda env create -f environment.yml```

Alternatively, you can install the libraries listed in ```requirements.txt``` however you see fit.


### Data

The dataset consists of 40,479 training images and 61,191 test images, and each image is a 256x256 pixel jpeg. The filetrain_v2.csv is included which liststhe training file names and their accompanying labels. The labels can be broken down into three categories: cloud coverlabels, common labels, and less common labels. There are 17 labels in total: clear, partly cloudy, cloudy, haze, primary, water, habitation, agriculture, road, cultivation, bare ground, slash and burn, selective logging, blooming, conventional mining, artisanal mining, and blow down. 

The data and all models I used to produce my final solution can be obtained by running the ```get_data.ipynb``` notebook.


### Usage

#### Getting the data

To reproduce my solution by training from scratch, you first must download the data by running the ```get_data.ipynb``` notebook.

#### Training the models

Then you can proceed to train the models by running the ```train.ipynb``` notebook. You will need to run this notebook five times, once for each of the following fastai models: resnet50, resnet101, resnet152, densenet121, densenet169. You can change which architecture you are using by changing the line in cell [8] to whichever pretrained model you wish to train, for example:

```arch = models.resnet152```

#### Creating an ensemble

To create an ensemble of the models you wish to include, you can run the ```create_ensemble.ipynb``` notebook. Simply define the ```model_list``` in cell [4] to include the models you wish like so:

```model_list = ['resnet50.pkl','resnet101.pkl', 'resnet152.pkl', 'densenet121.pkl', 'densenet169.pkl']```


#### Making a submission

To make predictions and submit to the Kaggle competition to see your score, run the notebook ```predict_and_submit.ipynb```. To submit directly from the notebook you will need the Kaggle command line tool installed. Directions on how to set this up can be found in the ```get_kaggle_data.ipynb``` notebook. Alternatively, you can manually submit to the competition by navigating to the competition page and select the .csv file you'd like to submit.

Note that in either case, you will need to accept the competitions terms before being able to submit to the competition.


