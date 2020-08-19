---
layout: post
category: blog
title:  "GeeksForGeeks - Circular Tour"
date:   2020-08-08
tags: algorithm must_do geeks
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/lru-cache/1">link</a>

## Problem
Suppose there is a circle. There are N petrol pumps on that circle. You will be given two sets of data.
1. The amount of petrol that every petrol pump has.
2. Distance from that petrol pump to the next petrol pump.
Find a starting point where the truck can start to get through the complete circle without exhausting its petrol in between.
Note :  Assume for 1 litre petrol, the truck can go 1 unit of distance.

## Solution
<pre><code><strong>struct petrolPump{
    int petrol;
    int distance;
};


int tour(petrolPump p[], int n){
    int start = 0, i = 0, pet = 0, loc = 0;
    while(start < n && i < n){
        pet += p[loc].petrol - p[loc].distance;
        ++i;
        if(pet < 0){
            ++start;
            i = 0;
            pet = 0;
        }
        loc = (start + i)%n;
    }
    if(pet >= 0 && i == n){
        return pet;
    }else{
        
    }
}
</strong></code></pre>
<strong>Time Complexity : <i>O(n)</i></strong>