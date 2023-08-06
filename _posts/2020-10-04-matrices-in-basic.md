---
layout: post
title: "Matrices in BASIC"
---

When it comes to retro-programming there are any number of languages to choose from, but for this topic we will use Atari Basic. Linear Algebra deals mainly with matrices and vectors. So, setting vectors aside for the time being, the first step is representing matrices in Atari Basic. Fortunately, Atari Basic provides two-dimensional arrays, which initially seem perfect for representing matrices.

```
10 M=4
20 N=3
30 DIM A(M,N)
40 FOR I=1 TO M
50 FOR J=1 TO N
60 READ D
70 A(I,J)=D
80 NEXT J
90 NEXT I
100 FOR I=1 TO M
110 FOR J=1 TO N
120 PRINT A(I,J);" ";
130 NEXT J
140 PRINT
150 NEXT I
1000 DATA 4,2,3
1010 DATA 5,1,2
1020 DATA 4,3,2
1030 DATA 3,2,5
```
MATRIX01.BAS

Lines 10 and 20 define the order of the matrix as 4 rows by 3 columns.

Line 30 uses a DIM statement to create an m by n (4 x 3) matrix.

Lines 40 through 90 read the data from that data statements on lines 1000 to 1030. To loops are used to do this the outer I loop increments for each row from 1 to M and the inner J loop increments for each column 1 to N. The data statements are organized in such away as to mirror the structure of the matrix.

Lines 100 through 150 loop over the matrix is a similar manner. For each iteration of the J loop another entry is printed to the screen along with a space to separate the values. The I loop separates each row by using a “standalone” PRINT statement on line 140 to insert a line break.

The code presented here is elementary. It uses some simple Atari Basic statements to read is a Matrix from DATA statements and then print the Matrix on screen. In future installments we will expand on these concepts to perform Matrix operation in ever increasing complexity.
