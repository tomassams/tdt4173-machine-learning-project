
----

# TDT4173 Project Assignment
## Image classification in the gastrointestinal tract
## Comparison of KNN and CNN
----

This is the public repository for our project in TDT4173 Machine Learning at NTNU, fall 2020.

The project uses the [Kvasir](https://datasets.simula.no/kvasir/) v2 dataset, which contains images from the gastrointestinal tract.

The included two notebooks are intended for use on Google Colab, but should be easily adjustable to run in local environments..

All packages should be pre-installed in the Colab notebook. If you need to run the notebook locally or elsewhere, all package requirements can be installed based on ```requirements.txt```. It is recommended that you do this inside a virtualenv or conda environment to avoid issues with existing packages.

To run the notebook in Google Colab, click "Open in Colab" at the top of the notebook.

## CNN visualization (extra)

We built a website to show how the CNN model process features in an image. 

The repository is available at https://github.com/tomassams/tdt4173-cnn-visualization 

A live demo is available at https://tdt4173-cnn-visualization.netlify.app/.

## Project structure

```txt
|-- LICENSE.md
|-- README.md                       <- The file you are reading now
|-- requirements.txt                <- List of python package dependencies
|-- project_notebook_knn.ipynb      <- Notebook containing KNN code used in the project
|-- project_notebook_cnn.ipynb      <- Notebook containing CNN code used in the project
|-- models                          <- Folder containing persisted models
|    |-- knn_pixel_intensity.pkl
|    |-- knn_color_histogram.pkl
|    |-- cnn_simple.hdf5
|    |-- cnn_resnet_tl.hdf5
|    |-- cnn_resnet_tl_tuned.hdf5
|-- data                            <- Folder containing the dataset (will be populated by the notebook)
|    |-- raw
|       |-- dyed-lifted-polyps
|       |-- dyed-resection-margins
|       |-- esophagitis
|       |-- normal-cecum
|       |-- normal-pylorus
|       |-- normal-z-line
|       |-- polyps
|       |-- ulcerative-colitis
|    |-- processed                  <- Raw dataset split into train/test (will be populated by the notebook)
|       |-- train
|       |-- test
|    |-- zip                        <- Original zip file with the dataset (will be populated by the notebook)
|-- results                         <- Folder containing prediction results and evaluation
|    |-- knn_pixel_intensity
|       |-- knn_pixel_intensity_confusion_matrix.png
|       |-- knn_pixel_intensity_classification_report.csv
|       |-- knn_pixel_intensity_gridsearch_report.csv
|    |-- knn_color_histogram
|    |-- cnn_simple
|    |-- cnn_resnet_tl
|    |-- cnn_resnet_tl_tuned
```

## Installing dependencies
Run the following command in your command line tool of choice:

```bash
pip install -r requirements.txt
```

## Loading trained models

All the trained models were persisted after training, and can be re-loaded into Sklearn or Keras to try them out yourself. Preprocessing steps can be found in the Colab notebook.

### KNN

```python
import pickle

# Replace with desired model path
model_path = 'models/knn_pixel_intensity.pkl'

# Load
loaded_model = pickle.load(open(model_path, 'rb'))

# Predict on data
loaded_model.predict(x_test)
```

### CNN

```python
from tensorflow import keras

# Replace with desired model path
model_path = 'models/simple_cnn.hdf5'

# Load
loaded_model = keras.models.load_model(model_path)

# Predict on data
loaded_model.predict(x_test)
```
