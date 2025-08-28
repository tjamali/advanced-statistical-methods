# Singular Value Decomposition (SVD)

## Application to Detrending Time Series

In time series analysis, identifying and removing trends is essential for uncovering the underlying scaling behavior. However, “trend” is not uniquely defined, and real-world data often mix deterministic trends with stochastic fluctuations and periodic components.

One well-known method, **Multifractal Detrended Fluctuation Analysis (MF-DFA)**, is powerful but not foolproof: it struggles with intrinsic periodicities. When sinusoidal components are present, MF-DFA produces *spurious crossovers* in the fluctuation function, leading to unreliable scaling exponents.
👉 To fix this, trends and periodic components must be attenuated before applying MF-DFA.

### Why SVD?

Several preprocessing methods exist (Fourier filtering, EMD, etc.). I use **Singular Value Decomposition (SVD)** because:

* It suppresses both periodic and quasi-periodic trends.
* It handles signals with multiple peaks in the power spectrum better than alternatives.
* It provides a clear separation between dominant structured components (large singular values) and stochastic fluctuations (smaller singular values).

Following the approach in [Xu et al., Phys. Rev. E 95, 062802 (2017)](https://doi.org/10.1103/PhysRevE.95.062802), I combine **SVD preprocessing with MF-DFA** to extract reliable multiscaling behavior in nanofriction data.

### How SVD Works (Intuition)

Every matrix $M$ can be decomposed into:

$$
M = U \Sigma V^*
$$

where $U$ and $V$ are rotations, and $\Sigma$ contains the singular values (rescaling factors).

* Large singular values → dominant patterns (often trends/periodicities).
* Smaller singular values → noise and fine-scale fluctuations.

By reconstructing the signal with only selected components, we filter out unwanted trends.

<p align="center">
  <img width="500" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Singular-Value-Decomposition.svg/800px-Singular-Value-Decomposition.svg.png" alt="SVD decomposition illustration">
</p>

### Implementation

I provide [notebook code in this repo](./notebooks/svd_detrending.ipynb) to demonstrate:

1. Computing the SVD.
2. Removing periodic components from synthetic and experimental signals.
3. Applying MF-DFA on the detrended series.

**Practical Insight:**
In my experiments, reconstructing the time series while omitting the top singular components effectively removes periodicities, yielding clean fluctuation functions without artificial crossovers.
