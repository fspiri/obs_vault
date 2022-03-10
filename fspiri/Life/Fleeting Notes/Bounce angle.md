# Bounce angle
#### how to calculate the bounce angle on an arbitrary wall
***
in the general case suppose your missile has velocity v and hits a wall with [[surface normal]] n.
![[c7WTq.png]]
split v into components u perpendicular to the wall and w parallel to it.
![[e6K3L.png]]
Where:

$$
\begin{gather*}
u = (v · n / n · n) n \\
w = v − u
\end{gather*}
$$

Here, $v · n$ is the [[dot product]] of the [[vector]]s v and n.
The dot product $n · n$ evaluates to the square of the length of the normal vectorl if you always keep your normals in the form of [[Unit Vector]]s then $n · n = 1$ and you can omit the division.

After bouncing, the component of motion parallel to the wall is affected by friction f, and the component perpendicular to the wall is addected by elasticity, which can be given in the form of a [[coefficient of restitution]] r.

So the velocity after the collision is : $v′ = f w − r u$. 
In a perfectly elastic, frictionless collision: $v′= w − u$; that is, the motion is reflected about the normal at the point of collision.

This approach works just the same in three dimensions too.

(This is a very simplified version of bouncing; it takes no account of angular momentum or deformation. But for many kinds of video games this kind of simplification is perfectly adequate.)
