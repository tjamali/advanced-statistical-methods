# Statistical Methods: Singular Value Decomposition

## Application for deterending time series

Recognizing trends and making proper detrending procedures are an important step toward robust analysis. 
There is no unique definition of the trend. Subsequently, any proper algorithm for extracting trends from
underlying data sets should remove embedded trends without destroying intrinsic fluctuations as much as 
possible. For real-world data sets the mentioned situation needs more precise considerations. It was 
demonstrated that Multifractal detrended fluctuation analysis (MF-DFA) is not able to eliminate the effect
of intrinsic periodic trends in data series. As a result, when MF-DFA applied to data with sinusoidal
trends, spurious crossover occurs in the plot of fluctuation function. It can be shown that a periodic
trend induces an artificial crossover at the scale of the sinusoidal periodicity. This crossover leads
to difficulties in analyzing data in a sense that it makes the estimation of scaling exponent unreliable.
Therefore, to measure the scaling exponent correctly, we have to minimize the effect of such trends in
the data before applying the MF-DFA. Along this line, various methods have been suggested including the
Fourier filtering method, the empirical mode decomposition (EMD) method, and the singular value decomposition
(SVD) technique. Here we use SVD because, comparing with the other two techniques, it reduces both periodic
and quasiperiodic trends in series with more than one peak in their power spectrums.

Every matrix *M* can be seen as a linear transformation. It is shown that this transformation can be decomposed
in three sub-transformations (using three another matrices *U*, <img src="https://latex.codecogs.com/svg.latex?\Sigma" />
, and <img src="https://latex.codecogs.com/svg.latex?V^*" />
): 1. rotation, 2. re-scaling,
3. rotation (See https://en.wikipedia.org/wiki/Singular_value_decomposition for more details. The follwoing figure is from this page).

<p align="center">
  <img width="600" height="540" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Singular-Value-Decomposition.svg/800px-Singular-Value-Decomposition.svg.png">
</p>
