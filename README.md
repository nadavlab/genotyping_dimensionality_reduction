# genotyping_dimensionality_reduction
Models for dimensionality reduction UKBB (and other) genotyping samples.

We have trained separate dimensionality reduction models for each of the 22 chromosomes (without the sex chromosomes), reducing the dimension of the SNPs to 10% of the input SNPs amount. We have used two models: Deep Auotoencoder (autoencoder) and Principal Component Analysis (PCA). We saved the trained dimensionality reduction models for future use without having to retrain.
For the use of the models, the SNPs order is substantial. We saved the SNPs we used and their input order for each chromosome. The files are available in: https://www.dropbox.com/home/genotyping_dimensionality_reduction_files/SNPs_order

## Autoencoder
For the Autoencoder, we trained the models with TensorFlow Python package, and the whole model was saved. It includes:
1. The model's architecture/config
2. The model's weight values
3. The model's compilation information
4. The optimizer and its state

The trained Autoencoder models for each chromosome are available in: https://www.dropbox.com/home/genotyping_dimensionality_reduction_files/Autoencoder

In order to load the model, use:
```
import tensorflow as tf
from tensorflow import keras

autoencoder = keras.models.load_model(auto_name)
#where auto_name is the Autoencoder file name
```
In order to use the model for dimensionality reduction, use:
```
encoder = autoencoder.get_layer('encoder')
codings = encoder.predict(X)
```
Where X is the SNPs data for which dimension reduction is required. X can be:
1. A Numpy array (or array-like), or a list of arrays (in case the model has multiple inputs).
2. A TensorFlow tensor, or a list of tensors (in case the model has multiple inputs).
3. A tf.data dataset.
4. A generator or keras.utils.Sequence instance. 

## PCA
For the PCA, we implemented the models with Scikit-learn package, and saved them using the methods described in model persistence Scikit-Learn.

The trained PCA models for each chromosome are available in: https://www.dropbox.com/home/genotyping_dimensionality_reduction_files/PCA

In order to load the model use:
```
import pickle
pca = pickle.load(open("pca_name.pkl",'rb'))
#where pca_name is the PCA file name
```
In order to use the model for dimensionality reduction, use:
```
codings = pca.transform(X)
```
Where X is the SNPs data for which dimension reduction is required. X should be a array-like of shape (n_samples, n_features).
