Solving MDPs

1. (a) 2 ^ 11
                    γ     s = A    s = E
(b) V3(s)          1.0    0        4
V10(s)             1.0    2        4
V10(s)             0.1    0        2.2
Q1(s,west)         1.0    ——        0
Q10(s,west)        1.0    ——        3
V ∗(s)             1.0     ∞         ∞
V ∗(s)             0.1     0        2.2
V∗10(A), γ = 1: In 10 time steps with no discounting, the rewards don’t decay, so the optimal strategy is to
climb the two stairs (-1 reward each), and then slide down the two slide squares (+2 rewards each). You only
have time to do this once. Summing this up, we get −1 − 1 + 2 + 2 = 2.
V∗10(E), γ = 1: No discounting, so optimal strategy is sliding down the slide. That’s all you have time for.
Sum of rewards = 2 + 2 = 4.
V∗10(A), γ = 0.1. The discount rate is 0.1, meaning that rewards 1 step further into the future are discounted
by a factor of 0.1. Let’s assume from A, we went for the slide. Then, we would have to take the actions
A → B,B → C,C → D,D → E,E → F, F → G. We get the first -1 reward from C → D, discounted by γ2
since it is two actions in the future. D → E is discounted by γ3, E → F by γ4, and F → G by γ5. Since γ
is low, the positive rewards you get from the slide have less of an effect as the larger negative rewards you get
from climbing up. Hence, the sum of rewards of taking the slide path would be negative; the optimal value is 0.

V∗10(E), γ = 0.1. Now, you don’t have to do the work of climbing up the stairs, and you just take the slide
down. Sum of rewards would be 2 (for E → F) + 0.2 (for F → G, discounted by 0.1) = 2.2.

Q∗10(E,west), γ = 1. Remember that a Q-state (s,a) is when you start from state s and are committed
to taking a. Hence, from E, you take the action West and land in D, using up one time step and getting an
immediate reward of 0. From D, the optimal strategy is to climb back up the higher flight of stairs and then
slide down the slide. Hence, the rewards would be −1(D → E) + 2(E → F) + 2(F → G) = 3.

V ∗(s), γ = 1. Infinite game with no discount? Have fun sliding down the slide to your content from
anywhere.

V ∗(s), γ = 0.1. Same reasoning apply to both A and E from V ∗
10(s). With discounting, the stairs are more
costly to climb than the reward you get from sliding down the water slide. Hence, at A, you wouldn’t want to
head to the slide. From E, since you are already at the top of the slide, you should just slide down.

                                                   Q(D, west)    Q(D, east)   Q(E, west)   Q(E, east)
(c) Initial:                                            0             0            0            0
Transition 1: (s = D, a = east, r = −1, s′ = E)                       -0.5
Transition 2: (s = E, a = east, r = +2, s′ = F)                                                 1.0
Transition 3: (s = E, a = west, r = 0, s′ = D)
Transition 4: (s = D, a = east, r = −1, s′ = E)                       -0.25

2. (a) 
Fp(s, up) = 1 + 2(1) = 3
Fp(s, left) = 1 + 2(0) = 1
Fp(s, right) = 1 + 2(0) = 1
Fp(s, stay) = 1 + 2(0) = 1
Fg(s, up) = 2 + 0 + 0 = 2
Fg(s, left) = 2 + 1 + 1 = 4
Fg(s, right) = 2 + 1 + 1 = 4
Fg(s, stay) = 2 + 0 + 2 = 4

(b)
Q(s, up) = wpFp(s, up) + wgFg(s, up) = 100(3) + (−10)(2) = 280
Q(s, left) = wpFp(s, left) + wgFg(s, left) = 100(1) + (−10)(4) = 60
Q(s, right) = wpFp(s, right) + wgFg(s, right) = 100(1) + (−10)(4) = 60
Q(s, stay) = wpFp(s, stay) + wgFg(s, stay) = 100(1) + (−10)(4) = 60

(c)
Qnew(s, a) = R(s, a, s′) + γ ∗ max
a′
Q(s′, a′)
= 250 + 0.5 ∗ max{Q(s′, down),Q(s′, stay)}
= 250 + 0.5 ∗ 0
= 250

where

Q(s′, down) = wpFp(s′, down) + wgFg(s′, down) = 100(0) + (−10)(2) = −20
Q(s′, stay) = wpFp(s′, stay) + wgFg(s′, stay) = 100(0) + (−10)(0) = 0

(d)
wp = wp + α ∗ (Qnew(s, a) − Q(s, a)) ∗ Fp(s, a) = 100 + 0.5 ∗ (250 − 280) ∗ 3 = 55
wg = wg + α ∗ (Qnew(s, a) − Q(s, a)) ∗ Fg(s, a) = −10 + 0.5 ∗ (250 − 280) ∗ 2 = −40