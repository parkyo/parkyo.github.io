---
layout: post
category: blog
title:  "Google Kick Start 2020 Round B - Robot Path Decoding"
date:   2020-06-29
tags: algorithm kick_start
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc8/00000000002d83dc">LINK</a>
<blockquote>Know how to use <code>mod</code> appropriately</blockquote>
## Problem
Your country's space agency has just landed a rover on a new planet, which can be thought of as a grid of squares containing 109 columns (numbered starting from 1 from west to east) and 109 rows (numbered starting from 1 from north to south). Let (w, h) denote the square in the w-th column and the h-th row. The rover begins on the square (1, 1).
<p>
The rover can be maneuvered around on the surface of the planet by sending it a program, which is a string of characters representing movements in the four cardinal directions. The robot executes each character of the string in order:

- N: Move one unit north.
- S: Move one unit south.
- E: Move one unit east.
- W: Move one unit west.

There is also a special instruction X(Y), where X is a number between 2 and 9 inclusive and Y is a non-empty subprogram. This denotes that the robot should repeat the subprogram Y a total of X times. For example:
2(NWE) is equivalent to NWENWE.
3(S2(E)) is equivalent to SEESEESEE.
EEEE4(N)2(SS) is equivalent to EEEENNNNSSSS.</p>

Since the planet is a torus, the first and last columns are adjacent, so moving east from column 109 will move the rover to column 1 and moving south from row 109 will move the rover to row 1. Similarly, moving west from column 1 will move the rover to column 109 and moving north from row 1 will move the rover to row 109. Given a program that the robot will execute, determine the final position of the robot after it has finished all its movements.

## Example
<pre><code><strong>input</strong>: 
4
SSSEEE
N
N3(S)N2(E)N
2(3(NW)2(W2(EE)W))</code></pre>
<pre><code><strong>output</strong>:
Case #1: 4 4
Case #2: 1 1000000000
Case #3: 3 1
Case #4: 3 999999995
</code></pre>

## Solution
- Keep track of the multipliers with a stack
- if <strong>w</strong> or <strong>h</strong> is out of the boundary, make sure to use the mod value in case of multipliers being bigger than multiples of 10^9
<pre><code><strong>int robotpath(){
    int tests;
    cin >> tests;
       for(size_t i = 0; i < tests; ++i){
           string line;
           long w=1,h=1;
           cin >> line;
           stack&lt;long&gt; mults;
           mults.push(1);
           for(char c : line){
               if(c == ')'){
                   mults.pop();
               }else if (c=='('){
                   continue;
               }else if(c == 'N'){
                   h -= mults.top();
                   if(h <= 0){
                       h = h % (long)pow(10,9) + (long)pow(10,9);
                   }
               }
               else if(c == 'S'){
                   h+= mults.top();
                   if(h > pow(10,9)){
                       h = h % (long)pow(10,9);
                   }
                   
               }else if(c == 'E'){
                   w+= mults.top();
                   if(w > pow(10,9)){
                       w = w % (long)pow(10,9);
                   }
               }
               else if(c == 'W'){
                   w-= mults.top();
                   if(w <= 0){
                       w = w % (long)pow(10,9) + (long)pow(10,9);
                   }
               }else{
                   long mult = mults.top() * ((int)c - 48);
                   mults.push(mult);
               }
               
           }
           cout << "Case #" << i+1 << ": " <<  w << " " << h << endl;
       }
       return 0;
}</strong></code></pre>
<strong>Time copmlexity: <i>O(t*n)</i></strong>




<!-- <pre><code> -->

