---
title: "Heuristic Search之Greedy Best First Search"
date: 2017-10-25T21:25:07+08:00
draft: false
tags: 
   - 算法
categories:
  - 技术
  - 归档
---

[TOC]


本篇文章介绍Greedy Best Fisrt Search算法。实现GBFS算法时使用了上篇文章介绍的优先队列。
下篇文章将尝试介绍著名的A star算法。

<!--more-->

## Greedy Best-First Search

- use heuristic function as evaluation function: f(n) = h(n)
- always expands the node that is closest to the goal node
- eats the largest chunk out of the remaining distance, hence, “greedy”

The following example is "Touring in Romania", which is an actual problem for making a plan travelling from Arad to Bucharest, the aim that we use the lowest cost.

![png](https://gitee.com/gdhu/prvpic/raw/master/Image_018.png)

## example

Touring in Romania: Heuristic

- HSLD(n) = straight-line distance to Bucharest straight-line distance: Euclidean distance
- distance to Bucharest because our goal is to be in Bucharest

![png](https://gitee.com/gdhu/prvpic/raw/master/Image_019.png)

**[table]**

- HSLD(Bucharest) = 0
- HSLD(Fagaras) = 176 < 211 driving distance
- HSLD(n) cannot be computed from the problem description, it represents
additional information

![png](https://gitee.com/gdhu/prvpic/raw/master/Image_020.png)

## What's wrong with GBFS?

for this problem: search proceeds straight to the goal node:

- minimal search cost
- but not the optimal path

## Compare to Uniform-Cost Search

- UCS: numbers start from 0 and increase – tendency to expand earlier nodes –
breadth-first tendency
- [UCS的介绍](http://intelligence.worldofcomputing.net/ai-search/uniform-cost-search.html#.WfHjqbpuIzM)
- GBFS: number start from high and decreases – tendency to expand later nodes
– depth-first tendency

## 参考资料

1. 数据结构与算法分析
2. 大话数据结构
3. [AI planning 课程资料](http://media.aiai.ed.ac.uk/Project/AIPLAN/)
4. [AI planning Vedio](https://open.ed.ac.uk/artificial-intelligence-planning/ 
)

## Code(GBFS)

Path Found:

Arad(366)-->Sibiu(253)-->Fagaras(176)-->Bucharest(0).

```java
package cn.edu.gdut.java.test;

import java.util.HashMap;
import java.util.Map;
import java.util.PriorityQueue;

/**
 * Created by HuGuodong on 2017/10/26.
 */

public class Graph {


    private Map<String, AdjList> graph;


    /**
     * test main
     *
     * @param args
     */
    public static void main(String[] args) {
        GBFS("Arad", "Bucharest");

    }

    /**
     * algorithm: Greedy Best First Search
     * Greedy Best-First Search
     * use heuristic function as evaluation function: f(n) = h(n)
     * always expands the node that is closest to the goal node
     * eats the largest chunk out of the remaining distance, hence, “greedy”
     * @param start start node
     * @param end   end node
     */
    public static void GBFS(String start, String end) {
        Graph roads = new Graph();
        roads.init();
        AdjList adjList = roads.graph.get(start);
        System.out.println("Greedy Best First Search Starts!");
        AdjNode startNode = findNode(adjList, start);
        System.out.print("start from node: \n" + start + "(" + startNode.cost + ")" + "-->");
        int totalCost = 0;
        while (adjList.size() > 0) {
            AdjNode nextNode = adjList.poll();
            int nodeCost = nextNode.cost;
            totalCost += nodeCost;

            System.out.print(nextNode.name + "(" + nodeCost + ")-->");
            adjList = roads.graph.get(nextNode.name);

            if (isExist(adjList, end)) {
                int lastNodeCost = adjList.poll().cost;
                totalCost += lastNodeCost;
                System.out.println(end + "(" + lastNodeCost + ").");
                System.out.println("find path! \ntotal cost is : " + totalCost);
                return;
            }
        }
    }

    /**
     * init Touring in Romania road map
     */
    public void init() {
        graph = new HashMap<>();

        String name = "Arad";
        int cost = 366;
        AdjList adjList = new AdjList();
        adjList.add(new AdjNode("Arad", 366));
        adjList.add(new AdjNode("Zerind", 374));
        adjList.add(new AdjNode("Sibiu", 253));
        adjList.add(new AdjNode("Timisoara", 329));
        graph.put(name, adjList);

        name = "Sibiu";
        adjList = new AdjList();
        adjList.add(new AdjNode("Fagaras", 176));
        adjList.add(new AdjNode("Rimnicu", 193));
        adjList.add(new AdjNode("Rimnicu", 380));
        graph.put(name, adjList);

        name = "Fagaras";
        adjList = new AdjList();
        adjList.add(new AdjNode("Sibiu", 253));
        adjList.add(new AdjNode("Bucharest", 0));
        graph.put(name, adjList);
    }

    /**
     * whether the node name is in the adjlist
     *
     * @param adjList
     * @param name
     * @return
     */
    public static boolean isExist(AdjList adjList, String name) {
        for (AdjNode n :
                adjList) {
            if (n.name.equals(name)) {
                return true;
            }
        }
        return false;
    }

    /**
     * find a node by name
     *
     * @param adjList
     * @param name
     * @return
     */
    public static AdjNode findNode(AdjList adjList, String name) {
        for (AdjNode n :
                adjList) {
            if (n.name.equals(name)) {
                return n;
            }
        }
        return null;
    }

}

/**
 * adjacent list
 * priority queue
 */
class AdjList extends PriorityQueue<AdjNode> {

}

/**
 * adjacent node
 */
class AdjNode implements Comparable<AdjNode> {
    String name;
    int cost;

    public AdjNode(String name, int cost) {
        this.name = name;
        this.cost = cost;
    }

    @Override
    public int compareTo(AdjNode o) {
        return Integer.compare(cost, o.cost);
    }

    @Override
    public String toString() {
        return "AdjNode{" +
                "name='" + name + '\'' +
                ", cost=" + cost +
                '}';
    }
}
```