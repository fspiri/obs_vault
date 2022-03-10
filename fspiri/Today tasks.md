# Daily To-Do
## 8 February
### Solve the bounce bug on the 'experiment01.jar'

**Source of the bug: **
when hitting a border the shape keeps refreshing its movement vector.
**Cause of the bug:** 
most likely is that there's a trigger that occurs when a side of the shape's hitbox is touching a border, but since the shape is rotating, then its hitbox costantly expanding and contracting.  So the trigger to change movement vector fires when the hitbox hits the border but the shape rotates and so it's again in the border an the movement vector updates again returning to the initial movement vector and so the shape gets stuck in the border with its movement vector going lets say from -1 to 1 costantly since its stuck in the border


**Solutions brainstorming**: 
- **Movement flag** 
	- **idea:** from the first interaction between the hitbox and the border there's a counter that starts, this counter prevents any more updates to the movement vector until its false. 
	- **possible problems:** what if the shape hits a corner where two borders are hit almost at the same time?
	- **implementation idea:** since the counter takes in consideration the update timing of the scene it must be implements in the main App class or passing the timing parameter to the MovimentoVettoriale class. Then when a new HitBorder trigger is detected the flag turns true (or false) and counts the scene updates. When it will reach the desired number it then returns to false(or true);
	- **efficiency:** performance-wise isn't that expensive since its a function that runs in $O(1)$. The possible down side is that is a 'brute force' way of dealing with the problem not acting on the real cause.
- **Not using a trigger**
	- **idea:** instead of checking for a flag there is a new pat of the code that every cycle calculates the distance of the shape from the borders and takes in consideration the 'reducing *distances*'; for example if the shape is reaching the right border then an arbitrary variable $right$ gets smaller every time, when it reaches an arbitrary $zero$ 
	- **bad idea since is the same as the current approach**
- **Predicting the shape's position**
	- **idea:** when the movement vector gets updated calculate the shape next position with the updated movement vector then see if the relevant direction distant from relevant border gets smaller that it previously was use the non-update movement vector, else use the newly calculated vector.
	- **example:** the shape is approaching the right border with an angle of $0˚$ (perpendicular to the right border) and fires the right border trigger. Then a method gets called in which, knowing that is the right border getting hit, it saves the current shape distance from the right border $d_1$ (a value <= 0), saves the current movement vector $v_1$ and asks the *calculateRectangularComponents()* method the new movement vector $v_2$ then proceeds calculating the shape's position after the $v_2$ vector displacement and calculate the new distance from right border $d_2$. 
	If $d_2 < d_1$ returns $v_1$, *else* returns $v_2$
	- **problems:** with a still shape this may work, what with a rotating shape? It may happen that the vector is right but then after the rotation, the shape's hitbox, gets out of bounds and the method thinks the movement vector is not right when in reality it is.
	- **efficiency:** in theory this will cost $O(1)$ once in a while. But that 1 is a series of not so easy calculations. May cause lags when hitting a border.
	- **doability:** doable in theory, real program implementation needs the code to be restructured in at-minimum the MovimentoVettoriale class
- **Static hitbox**
	- **idea:** instead of a hitbox using the shape rotation a static hitbox using as height and width the max diagonal.
	- **problem:** the bounce will not feel high-quality, the solution is kinda meh, even more if we consider that the program is more of a challenge rather than an objective
- **Change the hit triggers actuaction points**
	- **idea:** right now the triggers fire when the center of the shape and its range are greater than or smaller than borders relevant position. 
	
	- screenbounds gives the correct borders position

## 9 February
- [x] Deutsch
	- [x] Kapitel 5
	- [x] Kapitel 6
	- [x] Kapitel 7
	- [x] Kapitel 8
	- [x] Kapitel 9
	- [x] Täglichen Gedicht schreiben
- [ ] Change bed sheets
- [ ] Go to post office
## 10 February
- [x] Add movement options interface in the experiment01 app
- [x] Deutsch
	- [x] Kapitel 10
	- [x] Kapitel 11
	- [x] Kapitel 12
	- [x] Alle neue Wörter auf Anki kopieren
- [x] Change bed sheets
- [ ] Go to post office
## 12 February
- [ ] Deutsch	
	- [x] Kapitel 13
	- [x] Kapitel 14
	- [x] Kapitel 15
	- [x] Kapitel 16
"When you can't get something, you start believing you won't be happy until you do"
## 19 February
- [x] NALS
	- [x] UI
		- [x] merge the two settings things into one big
		- [x] make it emerge from bottom
## 20 February
- [ ] NALS
	- [ ] Bugs
		- [x] Fix the shape moving from a wtf position
	- [ ] UI
		- [x] solve the window animation bug
		- [ ] improve graphic of the advanced settings
## 23 February
- [ ] Deutsch
	- [ ] A2 kapitel 3
		- [x] Kursbuch
		- [ ] Übunsbuch
- [ ]  Vita
	- [x] andare alle poste per pacco 3loveplug
	- [x] scrive a 3loveplug
	- [ ] fare la spesa
	- [ ] cambiare lenzuola
- [ ] Coding
	- [ ] start the food calculating values using JDBMS 
 ## 8 March
- [ ]  Daily 4 hours of german
	- [x]  2 hours from 10.30/12.30
	- [ ]  2 hours 15.30/17.30
- [ ] set up the notes tidied in obsidian app