1 Towers of Hanoi
(A) One possible state representation would be to store three lists, corresponding to which discs are on which peg.
If we assume that the N discs are numbered in order of increasing size 1, ..., n, then we can represent each peg
as an ordered list of integers corresponding to which discs are on that peg.
(b) If there are k pegs and n disks, then the size of the state space is kn.
For this setup, the size is 3N.
(c) ([1, ..., n], [], [])
(d) We can pop the first integer from any list (i.e., peg) and push it onto the front of another list (peg), so long as
it is smaller than the integer currently at the front of the list being pushed to (i.e., peg being moved to).
(e) Is the state the same as ([], [], [1, ..., n])?

2 Search Algorithms in Action

(a) States Expanded: Start, A, C, D, Goal
Path Returned: Start-A-C-D-Goal
(b) States Expanded: Start, A, B, D, C, Goal
Path Returned: Start-D-Goal
(c) States Expanded: Start, A, B, D, C, Goal
Path Returned: Start-A-C-Goal
