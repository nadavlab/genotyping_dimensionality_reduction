# genotyping_dimensionality_reduction
Models for dimensionality reduction UKBB (and other) genotyping samples.

We have trained separate dimensionality reduction models for each of the 22 chromosomes (without the sex chromosomes), reducing the dimension of the SNPs to 10% of the input SNPs amount. We have used two models: Deep Auotoencoder (autoencoder) and Principal Component Analysis (PCA). We saved the trained dimensionality reduction models for future use without having to retrain.
The trained dimensionality reduction models for each chromosome are available in: https://www.dropbox.com/home/genotyping_dimensionality_reduction_files 

For the Autoencoder, we trained the models with TensorFlow Python package, and the whole models were saved. It includes:
1. The model's architecture/config
2. The model's weight values
3. The model's compilation information
4. The optimizer and its state

For the PCA, we implemented the models with Scikit-learn package, and saved them using the methods described in model persistence Scikit-Learn.
