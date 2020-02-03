---
title: "衍生谓词"
date: 2019-06-22T09:59:37+08:00
draft: false
tags: 
   - PLANNING
categories:
  - 技术
  - 归档
---

[TOC]

Derived Predicates.

<!--more-->

# Derived Predicates

在PDDL2.2中提出了衍生谓词

## Derived Predicates

Derived predicates have been implemented in several planning systems in the past, including e.g. UCPOP. They are predicates that are not affected by any of the actions available to the planner. Instead, the predicate's truth values are derived by a set of rules of the form if formula(x) then predicate(x). The semantics are, roughly, that an instance of a derived predicate (a derived predicate whose arguments are instantiated with constants; a fact, for short) is TRUE iff it can be derived using the available rules. An example for a derived predicate is an `above` predicate in the Blocksworld, which can be derived by the following rule:

```
if on(x,y) OR (exists z: on(x,z) AND above(z,y)) then above(x,y)
```

简单说，通过一个谓词on，衍生出另一个谓词above。

## Timed Initial Literals

Timed initial literals are a syntactically very simple way of expressing a certain restricted form of exogenous events: facts that will become TRUE or FALSE at time points that are known to the planner in advance, independently of the actions that the planner chooses to execute. Timed initial literals are thus deterministic unconditional exogenous events. Syntactically, we simply allow the initial state to specify -- beside the usual facts that are true at time point 0 -- literals that will become true at time points greater than 0. For example:

```
(:init (at 9 (shop-open)) (at 20 (not (shop-open))))
```

Timed initial literals are practically very relevant: in the real world, deterministic unconditional exogenous events are very common, typically in the form of time windows (within which a shop has opened, within which humans work, within which traffic is slow, within which there is daylight, within which a seminar room is occupied, within which nobody answers their mail because they are all at conferences, etc.).

时间初始文字。

## REF

[ref-1](http://idm-lab.org/wiki/icaps/ipc2004/deterministic/pddl.html)