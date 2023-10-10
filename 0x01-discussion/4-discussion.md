Game Trees

1. (A) (i)                5

                5                          4

                        
                              9      10      4      6


(ii) Edges that can be pruned: 10-2, 4-6

(B) (i)          64
         
          64         66                65

    (ii)  To move East: X + Y > 128
          To reach P4: X + Y = 129

The first thing to note is that, to pick A over B, value(A) > value(B).
Also, the expected value of the parent node of X and Y is (X+Y)/2
=⇒ min(65, (X+Y)/2 > 64)
          
=⇒ (X+Y)/2 > 64
So, X + Y > 128 =⇒ value(A) > value(B)
To ensure reaching X or Y , apart from the above, we also have (X+Y)/2 < 65

=⇒ 128 < X + Y < 130
So, X, Y ∈ N =⇒ X + Y = 129


2. (a) The transition function is as follows:
T(s, Stop,Done) = 1
T(0,Draw, s′) = 1/3 for s′ ∈ {2, 3, 4}
T(2,Draw, s′) = 1/3 for s′ ∈ {4, 5,Done}
T(3,Draw, s′) =
1/3 if s′ = 5
2/3 if s′ = Done
T(4,Draw,Done) = 1
T(5,Draw,Done) = 1
T(s, a, s′) = 0 otherwise

The reward function is

R(s, Stop,Done) = s, s ≤ 5
R(s, a, s′) = 0 otherwise

(b) States 0   2   3   4   5
    V0     0   0   0   0   0
    V1     0   2   3   4   5
    V2     3   3   3   4   5
    V3     10/3  3  3  4   5
    V4     10/3  3  3  4   5

(c) States  0      2      3      4      5
    π∗      Draw   Draw   Stop   Stop   Stop