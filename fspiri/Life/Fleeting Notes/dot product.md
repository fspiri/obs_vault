# Dot product
The dot product or scalar product is an algebraic operation that takes two equal-length sequences of numbers (usually [[coordinate vectors]]), and return a single number. 
### Definitions
**Algebrically**
is the sum of products of the corresponding entries of the two sequences of numbers.
$$
a · b = \sum _{i=1}^{n}{a_i b_i}=a_1 b_1+a_2 b_2+ ... + a_n b_n
$$
where n denotes the dimension of the vector space

If vectors are identified with row matrices, the dot product can be expressed as a matrix product

$$
a · b = ab^T
$$
where $b^T$ denotes the transpose of $b$.

**Geometrically**
it is the product of the Euclidean magnitudes of the two vectors and the cosine of the angle between them.
Note that these two definitions are the equivalent when using Cartesian coordinates. 

in Euclidean space, a Euclidean vector is a geometric object that possesses both a magnitude and a direction. A vector can be pictures as an arrow. its magnitude is its length, and its direction is the direction to which the arrow points. The magnitude of a vector $a$ is denoted by $||a||$. The dot product of two Euclidean vectors $a$ and $b$ is defined by:
$$
a · b = ||a|| ||b|| cos\phi
$$
where $\phi$ is the angle between a and b
in particular 
	- if the vectors $a$ and $b$ are [[orthogonal]] $a · b = 0$
	- if the vectors $a$ and $b$ are codirectional $a · b = ||a|| ||b||$
this implies that
$a · a = ||a||^2$
which gives
$||a|| = \sqrt[2]{a · a}$
![[440px-Inner-product-angle.svg.png]]
The name dot product stands for the symbol used in the center whereas scalar wmphasize that the result is a scalar, rather than a vector.