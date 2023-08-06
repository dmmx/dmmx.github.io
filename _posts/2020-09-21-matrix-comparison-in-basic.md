---
title: Matrix Comparison in BASIC
layout: post
---

In my previous post we looked at a small BASIC program that read in a matrix from data statements and then displayed the matrix on screen. In this post we will look at comparing two matrices.

By definition matrix A and matrix B are equal if all of the corresponding entries are equal. This definition can be expanded for all inequalities as well:

* A > B, if all corresponding entries in A are greater than all
  corresponding entries in B.
* A < B, if all corresponding entries in A are less than all
  corresponding entries in B.
* A >= B, if all corresponding entries in A are equal to or greater than all
  corresponding entries in B.
* A <= B, if all corresponding entries in A are equal to or less than all
  corresponding entries in B.
* A does not equal B if some corresponding entries in A are greater
  then corresponding entries in B, while some are less than.
  
The matrices A and B are also not equal if they have different
orders. For example if A is a 4 by 3 matrix and B is a 5 by 8
matrix, then A is not equal to B.

The following BASIC program implements these rules:

```
10 Am=3:An=2
20 Dim A(Am,An)
30 For I=1 To Am
40   For J=1 To An
50     Read D
60     A(I,J)=D
70   Next J
80 Next I
100 Data 2,1
110 Data 4,0
120 Data 3,2
200 Bm=3:Bn=2
210 Dim B(Bm,Bn)
220 For I=1 To Bm
230   For J=1 To Bn
240     Read D
250     B(I,J)=D
260   Next J
270 Next I
280 Data 2,1
290 Data 4,0
300 Data 3,2
480 Graphics 0
490 Print "MATRIX A"
495 Print "--------"
500 For I=1 To Am
510   For J=1 To An
520     Print A(I,J);" ";
530   Next J
540   Print 
550 Next I
590 Print 
593 Print "MATRIX B"
595 Print "--------"
600 For I=1 To Bm
610   For J=1 To Bn
620     Print B(I,J);" ";
630   Next J
640   Print 
650 Next I
700 Print
710 Print "ORDER OF MATRIX A: ";
720 Print Am;" x ";An
730 Print "ORDER OF MATRIX B: ";
740 Print Bm;" x ";Bn
745 Print 
750 If Am=Bm And An=Bn Then 800
760 Print "A <> B"
770 Print "A AND B DO NOT HAVE THE";
780 Print " SAME ORDER"
790 End 
800 M=Am:N=An:S=M*N
805 Eq=0:Gt=0:Lt=0:Dim Sym$(1)
810 For I=1 To M
820   For J=1 To N
821     Print "COMPARE A(";I;",";J;") TO B(";I;",";J;"): ";
830     If A(I,J)=B(I,J) Then Eq=Eq+1:Sym$="="
831     If A(I,J)>B(I,J) Then Gt=Gt+1:Sym$=">"
832     If A(I,J)<B(I,J) Then Lt=Lt+1:Sym$="<"
833     Print A(I,J);" ";Sym$;" ";B(I,J)
840   Next J
850 Next I
890 Print
900 If Eq=S Then 1000
901 If Gt=S Then 1010
902 If Lt=S Then 1020
903 If Eq+Gt=S Then 1030
904 If Eq+Lt=S Then 1040
910 Print "A <> B"
940 End
1000 Print "A = B":End
1010 Print "A > B":End
1020 Print "A < B":End
1030 Print "A >= B":End
1040 Print "A <= B":End
1050 End
```
COMPARE.BAS

This time the program listing was prepared using OSS BASIC XE which
provides some indentation and uses lowercase letters for better
readability. I like the indentation but I'm not sure about the
lowercase lettering.


Lines 10 - 300 load the matrices we want to compare into memory.

Lines 480 - 630 print the matrices to the screen.

Lines 700 - 790 print out the order of both matrices and compares the
two orders. If the orders are not the same, then the matrices are not
equal.

Lines 800 - 850 compare the corresponding entries. If the entries are
equal, 1 is added to `Eq` (Equals). If `A(i,j)` is greater than
`B(i,j)` then 1 is added to `Gt` (Greater Than). And finally if
`A(i,j)` is less than `B(i,j)` then 1 is added to `Lt` (Less Than).

Lines 900 - 904 use the counts `Eq`, `Gt`, and `Lt` to determine if
all the entries are equal, greater than, or less than. Lines 903 and
904 use the sum of `Eq` + `Gt`, and `Eq` + `Lt` respectively to
determine "equal to or greater than" and "equal to or less than". If
none of the if statements evaluate to true, the matrices are declared
not equal and the program ends.

Lines 1000 - 1040 simply display the result of the comparisons done in
lines 900 - 904.

  
