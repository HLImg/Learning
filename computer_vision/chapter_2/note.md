## Chapter 2 Image formation

###  2.1 Geometric primitives and transoformations

**2D points.** (pixel coordinates) can be denoted using a pair of values, $\mathbf x=(x, y)\in\mathcal R^2$, or alternatively

$$
\mathbf x = [x, y]^T
$$

2D points can also be represented using *homogeneous coordinates*, $\mathbf{\tilde x} = (\bar x, \bar y, \bar w) \in \mathcal P^2$, where vectos that differ only by scale are considered to be equivalent. $\mathcal P^2=\mathcal R^3 - (0, 0, 0)$ is called the **2D projective space**.

A homogeneous vector $\mathbf{\tilde x}$ can be converted back into an **inhomogeneous vector** $\mathbf x$ by dividing through by the last element $\bar w$, i.e., 

$$
\mathbf{\tilde x} = (\bar x, \bar y, \bar w)=\bar w(x, y, 1)=\bar w\bar x
$$

where $\mathbf {\bar x}=(x, y, 1)$ is the augmented vector. *Homogeneous points whose last element is $\bar w=0$ are called ideal points or points at infinity* and do not have an equivalent inhomogeneous representation.

![image-20231207205015396](https://qiniu.lianghao.work/image-20231207205015396.png)

**2D lines.** 2D lines can also be represented as follows.

$$
\mathbf {\bar x}\cdot \mathbf{\tilde I}=(x, y, 1)\cdot (a, b, c) = ax+by+c=0
$$

We can normalize the line equation vector so that $\mathbf I=(\hat n_x, \hat n_y, d)=(\hat{\mathbf n}, d)$ with $\|\mathbf{\hat n}\|=1$. In this case, $\mathbf {\hat n}$ is the normal vector perpendicular to the line and $d$ is its distance to the origin. (The one exception to this normalization is the line at infinity $\mathbf {\tilde I}=(0, 0, 1)$, which includes all (ideal) points at infinity. )

We can also express $\mathbf {\hat n}$ as a function of rotation angle $\theta, \mathbf{\hat n}=(\hat n_x, \hat n_y)=(\cos\theta,\sin\theta)$. This reprensentation is commonly used in **Hough transform line-finding algorithm**. The combination $(\theta, d)$ is also known as *polar coordinates*.

When using homogeneous coordinates, we can compute the intersection of two lines as 

$$
\mathbf{\tilde x} = \mathbf{\tilde I_1}\times \mathbf{\tilde I_2}
$$

where $\times$ is the **cross product operator**. Similarly, the line jointing two points can be written as 

$$
\mathbf{\tilde I} =\mathbf {\tilde x_1}\times \mathbf {\tilde x_2}
$$

 When trying to fit an intersection point to multiple lines or, conversely, a line to multiple points, **least squares techniques** can be used.

**2D conics.** There are other algebraic curves that can be expressed with simple polynomial homogeneous equations. For example, the *conic sections* (so called because they arise as the intersection of a plane and a 3D cone) can be written using a **quadric equation**.

$$
\mathbf{\tilde x}^T \mathbf Q\mathbf{\tilde x}=0
$$

Quadric equations play useful roles in the study of multi-view geometry and camera calibration.

**3D points.** Point coordinates in three dimensions can be written using inhomogeneous coordinates $\mathbf x=(x,y,z)\in \mathcal R^3$ or homogeneous coordinates $\mathbf{\tilde x}=(\bar x, \bar y,\bar z, \bar w) \in \mathcal P^3$.  It is sometimes useful to denote a 3D point using the augmented vector $\mathbf{\bar x}=(x, y, z, 1)$ with $\mathbf{\tilde x}=\bar w\mathbf{\bar x}$. 

**3D planes.** 3D planes can also be represented as homogeneous coordinates $\mathbf{\tilde m}=(a, b, c, d)$ with a corresponding plane equation.

$$
\mathbf{\tilde x}\cdot \mathbf{\tilde m}=(x,y,z,1)\cdot(a, b, c, d)=ax+by+cz+d=0
$$

As with the case of 2D lines, we can normalize the 3D plane equation as $\mathbf m=(\hat n_x, \hat n_y, \hat n_z, d)=(\mathbf{\hat n}, d)$ with $\|\mathbf{\hat n}\|=1$, and the plane at infinity $\mathbf{\tilde m}=(0, 0, 0, 1)$, which contains all the points at infinity, cannot be normalized. We can express $\mathbf{\hat n}$ as a function of two angles $(\theta,\phi)$

$$
\mathbf{\hat n}=(\cos\theta\cos\phi,\sin\theta\cos\phi,\sin\phi)
$$

![image-20231207222720295](https://qiniu.lianghao.work/image-20231207222720295.png)

**3D lines**. Lines in 3D are less elegant than either lines in 2D or planes in 3D. One possible representation is to use two points on the line, $(\mathbf p,\mathbf q)$. Any other point on the line can be expressed as a linear combination of these two points. 

$$
\mathbf r = (1-\lambda)\mathbf p + \lambda \mathbf q
$$