# Computational Geometry
## 01 - Convex Hull Algorithms
***Convex Hull***: 
>(math definition) for a 2D plane of coordinates a convex hull can be defines
>as the smallest convex shape that contains the given [[convex]]

### Intuitive Approach
**input:** all the points given.
**output:** the points that make up the convex hull.
**Idea:** for an algorithm that calculates the convex hull clockwise an approach is to start from two points with this observation: " $(p, q)$ is an edge of the $CH(S)$ convex hull if all the points in input lie on this edge or on its right. ".

***PSEUDOCODE: ***

	firstConvexHull(S){
	E = null //instantiate an empty array
	foreach (p,q) of SxS with p!=q do //test if (p,q) is an edge of CH(S)
		boolean valid = true	//set up a flag
			foreach r in S do{ //for each point
				if not(r strictly right of pq(vector) or r in pq) then
					valid = false
			}
			if valid then	
				E.add((p,q))
	}
	L = sorted(E) //L is a sorted list of the E array of vertices
	return L;
	}

to test if a point is on the right of the pq vector we must determine the determinant of: 
$$ 
\left( \begin{array}{ccc}
x_r &x_r &1 \\ 
x_p &x_p &1 \\
x_q &x_q &1
\end{array}\right) < 1
$$

if the determinant is $<1$ is on the right, if its $=1$ is on the line. Complexity: $(O(1))$
	- to sort the edges we use an arbitrary edge and then find the vertice starting from that and so on until we get to the start
**Running Time Analysis** : $n^3\Rightarrow$  trash and the algorithm is not robust.<br><br>
### Good Approach
***Graham Scan***
**Idea:**  first compute the highest part of the hull and then the lower part.
**how to split the two?** we sort them in [[lexicographic order]], if they have the same x then they're sorted form top to bottom.

***PSEUDOCODE***

			UpperConvexHull(S){
			S = S.sortedLexicographically();
			L = S<0 , 1>
			for i = 3 to n do
				L.append(S(i))
				while ( |L| > 2 AND last 3 pts in L .makeALeftTurn() ) do
					removeSecondLastPointFromL() 
					//only right turns are allowed for UpperConvexHull
			return L
			}
the algorithm for the lower part is the same but for the left turn that is right.

**Running time analysis**: 
- the sorting takes $O(nlogn)$
- the for loop $O(n)$ counting the amortized anlysis for the while loop 
CONCLUSION:
this algorithm takes $O(nlogn)$ to compute the convex hull is a robust way in 2D
### Other algorithms 
**GRAHAM MARCH's ALGORITHM (gift wrapping algorithm)**
is the best algorithm for small samples of vertices because it has a running time of $O(n*h)$ whre h is the number of vertices of the hull, so for small convex hull it take $O(n)$.
**THE CHAN ALGORITHM** 
takes it even lower with a running tme of O(nlogh), the logic is complex.

***

## 02 - Intersection and Sweep Line Algorithms
**Idea:** Using a sweep line that goes from top to bottom to scan all the intersections between a set of given segments