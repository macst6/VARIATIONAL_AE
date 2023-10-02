# VARIATIONAL_AE
We have made a variational encoder from the vanilla encoder so that we can make multivariate encoder
VAE represents a Deep Convolutional variational autoencoder architecture with
mirrored encoder and decoder components.


We are chnaging the structure of bottle neck of vanilla encoder
which was given as


For Vanilla AUTOENCODER
------------------------
------------------------


Function of bottleneck() -> Here we will add a bottle neck to our input 
-------------------------------------------------------------------------------------------


We get the input as 
[2,7,Width=7,Height=7,Num_channels=32]
but we want 
[Width=7,Height=7,Num_channels=32] which is the shape before bottle neck


We want to flatten data to add to bottleneck which is a dense layer
Data -> Flatten -> Pass to Bottleneck


and we get the x that will later be used in the for loop where we add the convolution layers with the encoder input 




For Variational AUTOENCODER
---------------------------
---------------------------



Changes done in functions 

Function of bottleneck() -> Here we will add a bottle neck to our input 
-------------------------------------------------------------------------------------------
Flatten data and add bottleneck with Guassian sampling (Dense layer).
mu is a dense layer according to its lantent dimension
Then we are trying to create log varaince
We are trying to perform computations in lambda layer where we have our sample points with our x
Whatever we passed in lambda layers then comes in the args
Epsilon is sample point from standard distribution 
#sample point = mu + Exp(log ((standard deviation)^2) / 2) * random normal distribution of random sample point





Function of reconstruction_loss() -> Here we are just checking difference between target and predicted values
--------------------------------------------------------------------------------------------------------------
Find RMSE

In reconstruction loss we take sqaure of error and we are specifying on which axis we are taking mean -> axis 1,2,3 




Function of kl_loss() -> Here we measure difference between two probability distribution
--------------------------------------------------------------------------------------------------------------
KL loss provides Symmetry and measures difference between two probability distribution
KL loss = 1/2 summation((1+log (std deviation)^2)-(mu^2)-(std deviation^2))   -> axis 1





Function of combined_loss() 
--------------------------------------------------------------------------------------------------------------
Here we are calculating all the loses
LOSS= aplha + RMSE + KL

aplha can be treated as a hyper-parameter to optimise

