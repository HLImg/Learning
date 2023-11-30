## Chapter 3

## Shallow neural networks

### 3.1 Neural network example

We define the shallow neural networks as functions $y=f_\phi(x)$ with parameters $\phi$ that map multi-variate inputs $x$ to multi-variate outputs $y$. The network has ten parameters $\phi = \{\phi_0, \phi_1, \phi_2, \phi_3, \theta_{10}, \theta_{11}, \theta_{20}, \theta_{21}, \theta_{30}, \theta_{31}\}$.


$$
\begin{aligned}
y &= f_\phi(x)\\
&= \phi_0+\phi_1a(\theta_{10 + \theta_{11}}x) + \phi_2a(\theta_{20} + \theta_{21}x) + \phi_3a(\theta_{30}+\theta_{31}x)
\end{aligned}
$$

where $a(\cdot)$ denotes the *activation function*. 

![image-20231130114040934](https://qiniu.lianghao.work/image-20231130114040934.png)



