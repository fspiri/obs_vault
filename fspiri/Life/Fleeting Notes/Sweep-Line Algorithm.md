# 02 Sweep-Line Algorithm
### for line segment Intersection

Problem: Given a set S of n closed non-overlapping line segments in the plane, compute...
- all points where at least two segments intersect and
- for each such point report all segments tat contain it.
How to do it?
![[Screenshot 2022-01-11 at 20.50.44.png]]

One way to do it is brute force, and it tae $n^2$, the best way to do so is by a "sweep-line" concept, a line that goes from top to bttom analyzing th segments.

This sweep line has to start from the top and go down, the moment it encounters a new segmentsit has to process, and so for the moment a segment ends, when it find an intersection it has to stop and process something.

Which active segments should be compared?
Only the neighbours.

What data structures should be used for this purpose?
- for the event (point) queue Q
	- p comes first tan q iff Yp > Yq, what is they come at the same Y? we use a slightly tilted sweep line:  Yp = Yq AND xp< xq.
	- store elements in a balanced binary search tree according to order of precedence, -> nextEvent() and del/insEvent() take O(log|Q|) time.
- for the (sweep line) status T
	- store the segments intersected by l in the-to-right order. In a balanced binary tree.
All the operations done take logarithmic time in the size of the data structure

***PSEUDOCODE***
findIntersections(S)
**Input:** set S of n non-overlappping closed line segments
**output:** - set I of intersection pts
						- for each p part of I every s part of S with p part of s (for each intersection points, all segments that contain that intersection point)

![[Screenshot 2022-01-11 at 21.19.35.png]]

	Q <- null; 
	T<- <vertical lines at x = -inf and x = +inf>; // sentinels
	foreach s in S do
		foreach endpoint p of s do
			if p is not in Q then Q.insert(p); L(p) = U(p) = C(p) = null;
			//lower part = blue
			//upper part = green
			//central = red
			if p lower endpt of s then L(p).append(s)
			if p upper endpt of s then! U(p).append(s)
			
	while Q!=null do
		p <- Q.nextEvent()
		Q.deleteEvent(p)
		handleEvent(p) //this is the real work
									//this is the core of the algorithm
									
subRoutine handleEvent(event p)
	
	handleEvent(event p)
	if |U(p) union L(p) union C(p)| > 1 then
		report intersection in p, repot segments in U(p) union L(p) union C(p)
	//what happens ater the sweep line moves over p? remove all blue and red segments
	delete L(p) union C(p) from T //consecutive in T!
	delete U(p) union C(p) into T in their order slightly below l
	//we can now have new neighbours
	if U(p) union C(p) = null then
		bleft/bright = left\right neighbor of p in T
		findNewEvent(bleft, bright, p)
	else
		sleft/sright = leftmost/rightmost segment in U(p) union C(p)
		bleft = left neighbor of sleft in T
		bright right neighbor of sright in T
		findNewEvent(bleft, sleft, p)
		findNewEvent(bright, sright, p)
	
	
	findNewEvent(s, s', p)
	if s intersection s' = null then return;
	{x} = s intersection s'
	if x below l or tothe right of p then
		if x is not in Q then Q.insert(x)
		if x is in rel-int(s) then C(x) <- C(x)union{s}
		if x is in rel-int(s') then C(x) <- C(x) union{s'}
		//rel-int: interia of
		
handleEvent if situation		
![[Screenshot 2022-01-11 at 21.32.10.png]]

handleEvent else situation
![[Screenshot 2022-01-11 at 21.33.28.png]]

Correctness of the Algortihm proff: 
lel
Running time Analysis
findIntersection
Q.insert takes O(log(Q)), at most nlogn, 
the while loop n(logn) in total
handleEvent
delete and insert are the bottlneck
the search for nighbors takes log time
findNewEvent
insert takes log

Observation how large can Q be in total?
2+(n(n-1)/2) event points = O(n^2)
T can have at most n eements

means that the bottleneck is O(logn^2) = O(2logn) = O(logn)

but how many times have the deletion and insertion to be performed? the running time is output sensitive: O((n + I)logn) time where I is the number of intersections.

the proof of this running time is accomplished through planar graphs

CONCLUSIONS
We can report all I intersection points among n non-overlapping line segments in the plane and report the segmnents involved in the intersections in O((n+ I)logn) time and O(n) space.