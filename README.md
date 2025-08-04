# Statistical Methods: Singular Value Decomposition

## Application to Detrending Time Series

Identifying and removing trends appropriately is essential for robust time series analysis. “Trend” is not uniquely defined, so any effective detrending algorithm must suppress embedded trends while preserving intrinsic fluctuations as much as possible. Real-world data complicate this balance, especially when periodic components are present.

It has been shown that Multifractal Detrended Fluctuation Analysis (MF-DFA) fails to fully remove intrinsic periodic trends. When applied to data containing sinusoidal components, MF-DFA produces spurious crossovers in the fluctuation function plot. A periodic trend induces an artificial crossover at the scale of that periodicity, which undermines reliable estimation of the scaling exponent. Therefore, to obtain accurate scaling exponents, such trends must be attenuated before applying MF-DFA.

Several preprocessing methods have been proposed for this purpose, including Fourier filtering, Empirical Mode Decomposition (EMD), and Singular Value Decomposition (SVD). Here we use SVD because, compared to the other two, it more effectively reduces both periodic and quasi-periodic trends in series that exhibit multiple peaks in their power spectra.

This work (see https://doi.org/10.1103/PhysRevE.95.062802) applies SVD in conjunction with MF-DFA to analyze nanofriction data and extract its multiscaling behavior.

Every matrix \( M \) represents a linear transformation. This transformation can be decomposed into three components via SVD: two rotations and a rescaling, using matrices \( U \), \( \Sigma \), and \( V^* \). (See the Wikipedia page on [Singular Value Decomposition](https://en.wikipedia.org/wiki/Singular_value_decomposition) for details. The figure below is adapted from that page.)

<p align="center">
  <img width="600" height="540" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Singular-Value-Decomposition.svg/800px-Singular-Value-Decomposition.svg.png" alt="SVD decomposition illustration">
</p>

**The notebook code provides the implementation details for computing the SVD.**
