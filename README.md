# tdt4173-machine-learning-project

This is the public repository for our project in TDT4173 Machine Learning at NTNU, fall 2020.

The included notebook is intended for use on Google Colab, but should be adjustable to run in local environments with a few tweaks in case of issues.

All packages should be pre-installed in the Colab notebook. You might need to pip install some packages if you run the notebook in a local or different environment.

To run the notebook in Google Colab, click "Open in Colab" at the top of the notebook.

## Project structure

```txt
|-- LICENSE.md
|-- README.md                       <- The file you are reading now
|-- project_notebook.ipynb          <- Notebook containing code used in the project
|-- models                          <- Folder containing persisted models
|    |-- knn_pixel_intensity.pkl
|    |-- knn_color_histogram.pkl
|    |-- cnn_simple.h5
|    |-- cnn_resnet_tl.h5
|    |-- cnn_resnet_tl_tuned.h5
|-- data
|    |-- raw                        <- Folder containing the dataset (will be populated by the notebook)
|       |-- dyed-lifted-polyps
|       |-- dyed-resection-margins
|       |-- esophagitis
|       |-- normal-cecum
|       |-- normal-pylorus
|       |-- normal-z-line
|       |-- polyps
|       |-- ulcerative-colitis
|-- results                         <- Folder containing prediction results and evaluation
|    |-- knn_pixel_intensity
|    |-- knn_color_histogram
|    |-- cnn_simple
|    |-- cnn_resnet_tl
|    |-- cnn_resnet_tl_tuned
```

## Loading persisted models

Note that these require that your input data matches the shapes the models are trained on.

See the notebook for preprocessing and feature extraction steps.

### KNN

```python
import pickle

loaded_model = pickle.load(open('./models/knn_pixel_intensity.pkl', 'rb'))
# loaded_model.predict(x_test)
```

### CNN

```python
from tensorflow import keras

loaded_model = keras.models.load_model('simple_cnn.h5')
# loaded_model.predict(x_test)
```