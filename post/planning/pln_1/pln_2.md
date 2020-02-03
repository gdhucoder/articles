---
title: "贝叶斯引论（二）"
date: 2017-10-21T21:25:07+08:00
draft: true
tags: 
   - PLANNING
   - BAYES
categories:
  - 技术
  - 归档
---

[TOC]

# Probabilistic models and probabilistic programs

A **probabilistic** model is a formal representation of a probability distribution over possible worlds.

The goal of probabilistic inference algorithms is to answer queries efficiently.

KEY DEFINITIONS
**Possible worlds**—All states you consider possible
**Probability distribution**—An assignment of a probability between 0 and 1 to each possible world, such that all of the probabilities add up to 1

**Probabilistic model**—A formal representation of a probability distribution over possible worlds
**Evidence**—Knowledge that you have about a specific situation
**Prior probability distribution**—The probability distribution before seeing any evidence
**Conditioning on the evidence**—The process of applying evidence to a probability distribution
**Posterior probability distribution**—The probability distribution after seeing the evidence; the result of conditioning
**Normalizing**—The process of proportionally adjusting a set of numbers so they add up to 1

# Modeling dependencies with Bayesian and Markov networks

概率编程的第五章：
1. 学习了directed dependencies in Figaro
2. 还没有学习完UNDIRECTED DEPENDENCIES IN FIGARO