# Dimensionality Reduction
## The Curse of Dimensionality

If you reduec the dimensionality of your training set before training a model, it will usually speed up training, but it may not always lead to better or simpler solution; it all depends on the dataset.


## Main Approcahes for Dimensionality Reduction

## Projection

Projecting a 3d training instance onto a 2d subspace.

## Manifold Learning

a d-dimensional manifold is a part of a n-dimensional space (where d<n) that locally resembles a d-dimensional hyperplane.

Many dimensionality reduction algorithms work by modelling the manifold on which the training instances lie; this is called manifold learning.

It relies on the manifold assumption, also called the manfold hypothesis, which holds that most real-world high-dimensional datasets lie close to a much lower-dimensional manifold.


## PCA

Principal component Analysis is by far the most popular dimensionality reduction algorithm. First it identifiers the hyperplane that lies closest to the data, and then it projects the data onto it.

## Preserving the variance

Before you can project the training set onto a lower-dimensional hyperplane, you first need to choose the right hyperplane.

Its reasonan=ble to select the axis that preserves the maximum amount o varuance, as it will most likely lose the leass information than other projections.

Another way to justify this choice is that it is the axis that minimizes the mean squred distance between the original dataset and its projection onto the axis.


## Principal Components

To find the principal component, there is a standard matric factorization technique called Sigular Value Decomposition (SVD) that can decompose the training set matrix X into the matrix multiplication of three matrices U E Vt where V contains all the principal components that we are looking for.


## Projecting Down to d Dimensions

Once you have identified all the principal components, you can reduce the dimesnionality of the dataset down to d dimensions by projecting i onto the hyperplane defined by the first d principal-components.

Selecting this hyperplane ensures that the projection will preserve as much variance as possible.

TO project the training set onto the hyperplane, you can simply compute the matrix multiplication of the training set matrix X by teh matrix W defined as the matrix xontaining the first d principal components.


## Explained Variance Ratio

This indiates the proportion of the datsets variance that lies along the axis of each principal component.


## Choosing the Right Number of Dimensions
Instead of arbitrarily choosing the number of dimesions to reduce down to, it is generally preferabble to choose the number of dimensions that add up to a sufficiently large portion of the variance.


You could set n_components and run PCA. However, there is a much better option: instead of specifying the number of principal components you want to preserverm you can set n_components to be a float 0.0 and 1.0 indicating the ratio of variance you wish to preserver.


## PCA for Compression

## Randomized PCA
If you set the svd_solver hyperparameter to "randomized", Scikit-learn uses a stochastic algorithm call Randomized PCA that quickly finds an approximation of the first d principal components.

## Kernel PCA
Kernel trick - a mathematical technique that implicityly maps instances into a very high-dimensional space(called feature space), enabling nonlinear classification and regression with Support Vetor machines.


## Selecting a Kernel and Tuning Hyperparameters
As kPCA is an unsupervised learning algorithm, there is no obvious performance measure to help you select the best kernel and hyperparametr values. 

However, dimensionality reduction is often a preparation step for a supervised learning task , so you can simply use grid search to select the kernel and hyperparamters that lead to the best performance on that task.


## LLE

Locally Linear Embediing is another very powerful nonlinear dimensionality reduction technique.

Its a manifold learning technique that does not rely on projections like other algorithms.

This makes it particularly good at unrolling twisted manifolds, specially where there is not too much noise.


## Other Dimensionality reduction Techniques

Multidimensional scaling: reduces dimesnionality while trying to preserve the distance between the instances.


Isomap:	creates a graph by connecting each instance to its nearest neighbors, then reduces dimensionality while rying to preserve the geodesic distances between the instances.


t-Distributed Stochastic Neighbor Embedding :- reduces dimensionality while trying to keep similar insances close and dissimilar instances apart. It is mostly used for visualization.


Linear Discriminant Analysis : - Its a ctually a classification algorithm, but during training it learns the most discriminative axes between the classes, and these axes can then be used to define a hyperplane onto which to project the data.
