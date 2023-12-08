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

If we use homogeneous coordinates, we can write the line as 

$$
\mathbf{\tilde r} = \mu\mathbf{\tilde p} +\lambda \mathbf{\tilde q}
$$

A specical case of this is when the second point is at infinity, i.e., $\mathbf {\tilde q}=(\hat d_x, \hat d_y, \hat d_z, 0)=(\mathbf{\hat d}, 0)$. We see that $\mathbf{\hat d}$ is the **direction** of the line. We can then re-write the inhomogeneous 3D line equation as 

$$
\mathbf r = \mathbf p + \lambda \mathbf{\hat d}
$$

A disadvantage of the endpoint representation for 3D lines is that it has too many degrees of freedom, i.e, six (three for each endpoint) instead of foud degrees that a 3D line truly has. *However, if we fix the two points on the line to lie in specific planes, we obtain a representation with four degrees of freedom*. 

If we wish to represent all possible lines without bias towards any particular orientation, we can use *Plucker coordinates*. These coordinatess are the six independent non-zero entries in the $4\times 4$ skw symmetric matrix

$$
\mathbf L = \mathbf{\tilde p}\mathbf{\tilde q}^T - \mathbf{\tilde q}\mathbf{\tilde p}^T 
$$

where $\mathbf{\tilde p}$ and $\mathbf{\tilde q}$ are any two (non-identical) points on the line. **This representation has only four degrees of freeedom**, since $\mathbf L$ is homogeneous and also satisfies $|\mathbf L|=0$, which results in a quadratic constraint on the Plucker coordinates.

**3D quadrics** The 3D analog of a conic sectyion is a quadric surface.

$$
\mathbf{\bar x}^T\mathbf Q\mathbf{\bar x}=0
$$

#### 2.1.1 2D transformations

**Translation.** 2D translations can be written as $\mathbf x'=\mathbf x + \mathbf t$ or

$$
\mathbf x'=[\mathbf I\ \mathbf t]\bar{\mathbf x},
$$

when $\mathbf I$ is the ($2\times 2$) identity matrix or

$$
\mathbf{\bar x}’ = \left[\array{
\mathbf I, \mathbf t\\
0^T, 1
}\right]
$$

using a $2\times 3$ matrix results in a more compact notation.

**Rotation + translation.** This tranaltion is also know as *2D regid body motion* or the *2D Euclideab transformation*. It can be written as $\mathbf x'=\mathbf R\mathbf x+t$ or

$$
\mathbf x' = \left[\array{
\mathbf R & \mathbf t
}\right]\mathbf{\bar x}
$$

where $\mathbf R$ is an **orthonormal rotation matrix** with $\mathbf {RR^T}=1$ and $|\mathbf R|=1$

$$
\mathbf R=\left[\array{
\cos\theta & -\sin\theta\\
\sin\theta &  \cos\theta
}\right]
$$

**Scaled rotation.** Also known as the similarity transformation, this transformation can be expressed as $\mathbf x'=s\mathbf R\mathbf x+\mathbf t$, where $\mathbf s$ is an arbitrary scale factor. It can also be written as 
$$
\mathbf x' = [s\mathbf R, \mathbf t]\mathbf{\bar x} =\left[\array{
a & -b & t_x\\
b & a & t_y
}\right] \mathbf{\bar x}
$$
where we no longer require that $a^2+b^2=1$. **The similarity transform preserves angles between lines**.

**Affine.** The affine transformation is written as $\mathbf x'=\mathbf A\bar{\mathbf x}$, where $\mathbf A$ is an arbitrary $2\times 3$ matrix, i.e.
$$
\mathbf x' =\left[\array{
a_{00} & a_{01} & a_{02}\\
a_{11} & a_{11} & a_{12}
}\right] \mathbf{\bar x}
$$
**Parallel lines remain parallel under affine transformations**.

**Projective.** This transformation, also known as a **perspective transform or homography**, operates on **homogeneous coordinates**.
$$
\mathbf{\tilde x'}=\mathbf{\tilde H'}\mathbf{\tilde x}
$$
where $\mathbf{\tilde H}$ is an arbitrary $3\times 3$ matrix. Note that $\mathbf{\tilde H}$ is **homogeneous**. The resulting homogeneous coordinate $\mathbf{\tilde x'}$ must be normalized in order to obtain an inhomogeneous result $\mathbf x$. 
$$
x'=\frac{h_{00}x+h_{01}y+h_{02}}{h_{20}x+h_{21}y+h_{22}}, y'= \frac{h_{10}x+h_{11}y+h_{12}}{h_{20}x+h_{21}y+h_{22}}
$$
*Perspective transformations preserve straight lines*.

**Hierarchy of 2D transformations.** 

![image-20231208211655869](https://qiniu.lianghao.work/image-20231208211655869.png)

**Co-vectors.** Consider the homogeneous equation $\mathbf{\tilde I}\cdot \mathbf{\tilde x}=0$. If we transform $\mathbf{\tilde x'}=\mathbf{\tilde H}\mathbf{\tilde x}$, we obtain
$$
\mathbf{\tilde I}\cdot \mathbf{\tilde x'}=\mathbf{\tilde I'^T}\mathbf{\tilde H}\mathbf{\tilde x} = (\mathbf{\tilde H^T\mathbf{\tilde I'}})^T\mathbf{\tilde x} = \mathbf{\tilde I}\cdot \mathbf{\tilde x}=0
$$
i.e., $\mathbf{\tilde H}’ = \mathbf{\tilde H^{-T}}\mathbf{\tilde I}$. **Projective transformation matrices are homogeneous**.

**Stretch/squash.** This transformation changes the **aspect ratio** of an image.
$$
\begin{aligned}
x' &= a_0 + a_1x + a_2y + a_6x^2 + a_7xy\\
y' &= a_3 + a_4x + a_5y + a_6xy + a_7y^2
\end{aligned}
$$
**Bilinear interpolant.** This eight-parameter transform
$$
\begin{aligned}
x' &= a_0 + a_1x + a_2y + a_6xy\\
y' &= a_3 + a_4x + a_5y + a_7xy
\end{aligned}
$$
can be used to intepolate the deformation due to the motion of the four corner points of a square. (In fact, it can interpolate the motion of any four non-collinear points.) *While the deformation is liear in the motion parameters, it does not generally preserve straight lines (only lines parallel to the squiare axes)*.

