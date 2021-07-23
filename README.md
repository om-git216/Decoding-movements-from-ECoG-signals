# Decoding movements from ECoG signals

Dataset used: ECoG data collected by the Kai Miller group at University of California, San Diego. This data has been used by Gerwin Schalk in the following paper:Schalk, G., et al. "Decoding two-dimensional movement trajectories using electrocorticographic signals in humans." Journal of neural engineering 4.3 (2007): 264.  

Here I will try to use the ECoG data to decode the kinematics of the cursor from the neural data. 

**Abstract:**

Previous research has shown that ECoG signals recorded from subjects moving a joystick while trying to track a target point can be used in order to decode the position of the cursor [1]. Methods like autoregressive models have been used before [1] and here I try to reproduce the results to decode cursor positions from ECoG signals using different methods - those of spectral analysis, feature analysis and linear regression to decode kinematic data from ECoG signals recorded in patients with intractable seizures. Due to the inter-subject differences in recording from different brain regions and the different channel counts per subject, I will train an individual model per subject.
As a part of the spectral analysis, I will calculate the power spectral density for each voltage channel. The spectral frequency has been categorised into seven bands - 8–12 Hz, 18–24 Hz (beta), 35–42 Hz, 42–70 Hz, 70–100 Hz, 100–140 Hz, 140–190 Hz  in the mu, beta and gamma frequency bands, similar to those used in [2]. Following this, I will calculate kinematic variables like position and velocity of the cursor. Then I will correlate these variables with the features extracted from the neural data. I will fit a simple linear regression model in order to do so. If this model performs poorly, I will go on to use sophisticated machine learning models to predict the kinematics of the cursor from the neural data. These analyses will provide yet another method that can be used in training BCIs.

**References:**

[1] G Schalk et al 2007 J. Neural Eng. 4 264
[2] Encoding of Movement Direction in Different Frequency Ranges of Motor Cortical Local Field Potentials Jörn Rickert, Simone Cardoso de Oliviera, Eilon Vaadia, Ad Aertsen, Stefan Rotter, Carsten Mehring Journal of Neuroscience 28 September 2005, 25 (39) 8815-8824.

**Methodology:**

1. Use a spectral analysis to extract frequency features from the data. Divide the data into four frequency bands - 42–70 Hz, 70–100 Hz, 100–140 Hz, 140–190 Hz and calculate the average power of each spectrum. 
2. Extract features from the cursor positions (X-position of the cursor).
3. Train a Linear Regression model with Lasso regularisation to predict cursor positions from neural data. 

**Results:**

1. Linear Models with Lasso regularisation fit the data better than those without Lasso Regularisation. 
2. The space of non linear models that can be fit to data is smaller than what was believed earlier. 
