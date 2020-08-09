---
layout: post
category: blog
title:  "GeeksForGeeks - LRU Cache"
date:   2020-08-08
tags: algorithm must_do
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/lru-cache/1">link</a>

## Problem
The task is to design and implement methods of an LRU cache. The class has two methods get() and set() which are defined as follows.
get(x)   : Returns the value of the key x if the key exists in the cache otherwise returns -1.
set(x,y) : inserts the value if the key x is not already present. If the cache reaches its capacity it should invalidate the least recently used item before inserting the new item.
In the constructor of the class the size of the cache should be intitialized.

## Solution
Use <strong>Doubly Linked List</strong> and <strong>Unordered Map</strong>.
<strong>DLL</strong> gives the advantage of removing nodes and changing the order while <strong>map</strong> can efficiently find if a key exists in the list.
<pre><code><strong>struct Node{
    int key;
  int value;
  Node* next;
  Node* prev;
  
  Node(int key, int value):key(key), value(value){}
};

class LRUCache
{
private:
    Node* last;
    Node* first;
    unordered_map&lt;int, Node*&gt; map;
    int size;

public:
    LRUCache(int cap):size(cap)
    {}
    
     int get(int key)
    {
        // this function should return value corresponding to key
        auto it = map.find(key);
        if(it != map.end()){
            Node* cur = it->second;
            if(cur->prev){
                (cur->prev)->next = cur->next;    
            }
            if(cur->next){
                (cur->next)->prev = cur->prev;    
            }
            cur->next = first;
            first->prev = cur;
            first = cur;
            return (it->second)->value;
        }
        return -1;
    }
    
     void set(int key, int value)
    {
        // storing key, value pair
        
        auto it = map.find(key);
        if(it == map.end()){
            if(map.size() == size){
                int rem_key = first->key;
                auto it = map.find(rem_key);
                if(first->next){
                    (first->next)->prev = nullptr;    
                }
                first = first->next;
                map.erase(it);
            }
            Node* n = new Node(key, value);
            last->next = n;
            n->prev = last;
            last = n;
            if(!first){
                first = n;
            }
            map.insert(pair&lt;int,Node*&gt;(key, n));
        }else{
            Node* n = it->second;
            if(n->prev){
                (n->prev)->next = n->next;
            }
            if(n->next){
                (n->next)->prev = n->prev;
            }
            last->next = n;
            n->prev = last;
            last = n;
            if(first == n && map.size() > 1){
                first = n->next;
            }
        }
    }
};</strong></code></pre>