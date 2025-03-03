### Hessian Calculation with Finite Differences

This can be done using 32-bit and 64-bit floating point arithmetic (the code for these are shown in their respective files). The folder **exponential_curve_with_mofd** compares the results of this method with the other approaches available.

The graphs show the accuracy of Hessian approximation using the Method of Finite Differences as a function of the size of perturbation parameter used.

The code is designed using float-64 arithmetic in an attempt to improve the precision of the final calculations.

The difference between matrices is measured according to the sum of the absolute differences between corresponding elements of each matrix. In code:


```
difference = torch.sum(torch.abs(mofd_hess-lib_hess))
```


These are evaluated for several network architectures, all of which are based on the architecture used to train a NODE to fit an exponential curve. The architecture is varied according to activation function, dimensionality of the latent space, and prior functionality of the input state (i.e. the network f acts as f(y) or f(y^3). The full details are as follows:



*   Figure 1: `Tanh()` activation function, 1 dim latent space, 4 parameters, f(y)
*   Figure 2: `Sigmoid()` activation function, 1 dim latent space, 4 parameters, f(y)
*   Figure 3: `ReLU()` activation function, 1 dim latent space, 4 parameters, f(y)
*   Figure 4:  `Tanh()` activation function, 1 dim latent space, 4 parameters, f(y^3)
*   Figure 5: `Sigmoid()` activation function, 1 dim latent space, 4 parameters, f(y^3)
*   Figure 6: `ReLU()` activation function, 1 dim latent space, 4 parameters, f(y^3)
*   Figure 7:`Tanh()` activation function, 2 dim latent space, 7 parameters, f(y)
*   Figure 8: `Sigmoid()` activation function, 2 dim latent space, 7 parameters, f(y)
*   Figure 9: `ReLU()`activation function, 2 dim latent space, 7 parameters, f(y)
*   Figure 10:  `Tanh()`activation function, 2 dim latent space, 7 parameters, f(y^3)
*   Figure 11: `Sigmoid()` activation function, 2 dim latent space, 7 parameters, f(y^3)
*   Figure 12: `ReLU()` activation function, 2 dim latent space, 7 parameters,f(y^3)

Another important point to note is that plots 6,9,12 all use a `ReLU()` activation function and have a Hessian containing purely zeros. The reason for this is likely to do with 'dead' neurons.

