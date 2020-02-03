---
title: "概率编程"
date: 2017-10-26T21:25:07+08:00
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

This chapter covers:

- The definition of a probabilistic model

- How probabilistic models are used to answer queries

- The ingredients of a probabilistic model, including variables, dependencies, functional 
forms, and numbers - How a probabilistic program represents the ingredients of a probabilistic model

4.1 Probabilistic models defined
A probabilistic model is a way of encoding the general knowledge you have of an uncertain situation.

4.1.1 Expressing general knowledge as a probability distribution over possible worlds

4.1.2 Exploring probability distributions further

KEY DEFINITIONS
Possible worlds—All states you consider possible
Probability distribution—An assignment of a probability between 0 and 1 to
each possible world, such that all of the probabilities add up to 1
Probabilistic model—A formal representation of a probability distribution over
possible worlds
Evidence—Knowledge that you have about a specific situation
Prior probability distribution—The probability distribution before seeing any
evidence
Conditioning on the evidence—The process of applying evidence to a probability
distribution
Posterior probability distribution—The probability distribution after seeing the
evidence; the result of conditioning
Normalizing—The process of proportionally adjusting a set of numbers so they
add up to 1

The ingredients of probabilistic models:
Variables
Dependencies
Functional forms
Numerical parameters
