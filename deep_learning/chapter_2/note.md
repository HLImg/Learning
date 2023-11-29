## Chapter 2

## Supervised learning

A supervised learning model defines a mapping from one or more inputs to one or more outputs. The model is just a mathematical equation; when the inputs are passed through this equation, it computes the output, and this is termed **inference**. The model equation also contains parameters. 

### 2.1 Supervised learning overview

In supervised learning, our goal is to build a model, denoted as $f_{\phi}(\cdot)$, that takes an input $\mathbf x$ and outputs a prediction $\mathbf y$. 


$$
\mathbf y = f_\phi(\mathbf x)
$$


where the $\phi$ represents the model's parameters.

### Notes

> **Loss functions vs. cost functions**: In much of machine learning books, the terms of loss function and cost function are used interchangeably.  However, more properly, a loss function is the individual term associated with a data point, and the cost function is the overall quantity that is minimized. *A cost function can contain additional terms that are not associated with individual data points*.

> **Generative vs. discriminative models**: The models $\mathbf y=f_\phi(\mathbf x)$ are **discriminative models**. These make an output prediction $\mathbf y$ from real-world measurements $\mathbf x$. Another approach is to build a **generative model** $\mathbf x = g_\phi(\mathbf y)$, in which the real-world measurements $\mathbf x$ are computed as a function of the output $\mathbf y$.
>
> - The generative approach has the disadvantage that it doesn't directly predict $\mathbf y$. To perform inference, we must invert the generative equation as $\mathbf y = g^{-1}_\phi(\mathbf x)$, and this may be difficult. 
> - The generative models have the advantage that **we can build in prior knowledge about how the data were created**. 
>
> In fact, discriminative models dominate modern machine learning; the advantage gained from exploiting prior knowledge in generative models is usually trumped by learning very flexible discriminative models with large amounts of training data.