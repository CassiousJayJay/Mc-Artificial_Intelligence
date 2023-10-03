1 Search and Heuristics

(a) The size of the state space is 4MN(Vmax + 1). The state representation is (direction facing, x, y, speed). Note that the speed can take any value in {0, ..., Vmax}.
(b) No, Manhattan distance is not an admissible heuristic. The agent can move at an average speed of greater than 1 (by first speeding up to Vmax and then slowing down to 0 as it reaches the goal), and so can reach the goal in less time steps than there are squares between it and the goal. A specific example: A timestep 0, the agent’s starts stationary at square 0 and the target is 9 squares away at square 9. At timestep 0, the agent takes the fast action and ends up at square 1 with a velocity of 1. At timestep 1, the agent takes the fast action and ends up at square 3 with a velocity of 2. At timestep 2, the agent takes the fast action and ends up at square 6 with a velocity of 3. At timestep 3, the agent takes the slow action and ends up at square 8 with a velocity of 2. At timestep 4, the agent takes the slow action and ends up at square 9 with a velocity of 1. At timestep 5, the agent takes the slow action and stays at square 9 with a velocity of 0. Therefore, the agent can move 9 squares by taking 6 actions.
(c) There are many answers to this question. Here are a few, in order of weakest to strongest:
(a) The number of turns required for the agent to face the goal.
(b) Consider a relaxation of the problem where there are no walls, the agent can turn, change speed
arbitrarily, and maintain constant velocity. In this relaxed problem, the agent would move with
Vmax, and then suddenly stop at the goal, thus taking dmanhattan/Vmax time.
(c) We can improve the above relaxation by accounting for the acceleration and deceleration dynamics.
In this case the agent will have to accelerate from 0 from the start state, maintain a constant velocity of Vmax, and slow down to 0 when it is about to reach the goal. Note that this heuristic will always return a greater value than the previous one, but is still not an overestimate of the true cost to reach the goal. We can say that this heuristic dominates the previous one. In particular, let us assume that dmanhattan is greater than and equal to the distance it takes to accelerate to and decelerate from Vmax (In the case that dmanhattan is smaller than this distance, we can still use dmanhattan/Vmax as a heuristic). We can break up the dmanhattan into three parts: daccel, dVmax, and ddecel. The agent travels a distance of daccel when it accelerates from 0 to Vmax velocity. The agent travels a distance of ddecel when it decelerates from Vmax to 0 velocity. In between acceleration and deceleration, the agent travels a distance of dVmax = dmanhattan − daccel − ddecel. daccel = 1 + 2 + + Vmax = (Vmax)(Vmax+1) 2 and ddecel = (Vmax − 1) + (Vmax − 2) + ... + 1 + 0 = (Vmax)(Vmax−1)
2 . So dVmax = dmanhattan − (Vmax)(Vmax+1)
2 − (Vmax)(Vmax−1)
2 = dmanhattan − V 2
max. It takes Vmax steps to travel the initial daccel, dmanhattan−V 2 max Vmax steps to travel the middle dVmax and Vmax steps to travel the last ddecel. Therefore, our heuristic is

(d) If the heuristic function is bounded, then A* graph search would visit all the nodes eventually, and would find a path to the goal state if there exists one. An inadmissible heuristic does not guarantee optimality as it can make the good optimal goal look as though it is very far off, and take you to a suboptimal goal
(e) Although admissible heuristics guarantee optimality for A* tree search, they do not necessarily guarantee optimality for A\* graph search; they are only guaranteed to return an optimal solution if they are consistent as well.
(f) The time to solve an A\* search problem is a function of two factors: the number of nodes expanded, and the time spent per node. An inadmissible heuristic may be faster to compute, leading to a solution that is obtained faster due to less time spent per node. It can also be a closer estimate to the actual cost function (even though at times it will overestimate!), thus expanding less nodes. We lose the guarantee of optimality by using an inadmissible heuristic. But sometimes we may be okay with finding a suboptimal solution to a search problem.

CSPs
(a) Binary:
X1 = P or X2 = P, X2 = E or X3 = E,
X3 = E or X4 = E, X4 = P or X5 = P,
X5 = P or X6 = P, X1 = P or X6 = P,
∀i, j s.t. Adj(i, j) ¬(Xi = E and Xj = E)
Unary:
X2 ̸= P,
X3 ̸= P,
X4 ̸= P

(b)
(c) X1 or X5 (tie breaking)
(d) (P,E,G,E,P,G)
(P,G,E,G,P,G)
