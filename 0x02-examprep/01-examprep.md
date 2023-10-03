Q1. SpongeBob and Pacman (Search Formulation)

(A)  
(i) 28mn \* 2^mn, There are 𝑚𝑛 positions in total. At each legal position, there are 7 possible speeds (0, 1, 2, 3, 4, 5, 6), so a factor
of 7 is multiplied. In addition, since change of direction depends on orientation of the car, another factor of 4 is
multiplied.
The only sequence of actions which guarantees that Pacman is caught is a sequence of actions which visits every
location. Thus, we also need to a list of 𝑚 ∗ 𝑛 boolean to keep track of whether we have visited a specific grid
location, and that is another factor of 2𝑚𝑛

(ii) 9, 3 possible throttle inputs, and 3 possible steering inputs. The list of boolean does not affect the branching factor.

(iii) Depth First Graph Search
Breadth First Tree Search
Breadth First Graph Search
(iv) yes
(B)
(i) None of the above
In this question, we only need one boolean list of size 𝑚𝑛 to keep track of whether we have visited a specific grid
location. So the size of the state space is bounded by 𝑁𝑝 = (28𝑚𝑛)𝑝2𝑚𝑛, which is none of the above.
(ii) 𝑏𝑝 = (𝑏1)𝑝
For example, the case of 𝑝 = 2 means two cars can do all 9 options, so the branching factor is 92 = 81. In general,
the branching factor is then 𝑏𝑝1

Q2
(a)
(i) True
(ii) True
(iii) True
(iv) Yes

(B)
(i)The current location of Scorpblorg
An array of numbers indicating how many times each snail has been visited so far

(ii) True
(iii) True
(iv) No

(C)
(i) Yes
(ii) No
