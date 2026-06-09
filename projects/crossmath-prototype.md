---
layout: post
title: 'Crossmath Prototype'
---
## Crossmath Prototype

**Role**: Solo Developer (Programming, Audio)

**Format**: Math Puzzle Game for Mobile and Web

**Project Timeline**: 1 Week (June 2026)


#### Project Overview

CrossMath is an arithmetic puzzle game that merges crossword topology with mathematical equations. Built to feature both infinite gameplay and curated progression, the project balances a high-performance procedural generation pipeline with a robust, data-driven level editor and JSON serialization system.

The project was intentionally designed to address two primary technical goals: mastering decoupled, data-driven architecture and maximizing design efficiency through custom Unity engine tools.

#### Challenges & Solutions

**Overcoming Procedural Deadlocks in Mixed Arithmetic**

The biggest technical hurdle was integrating multiplication and division into a cross-intersecting, procedurally generated loop.

The Problem: Initial brute-force iterations selected numbers randomly. If a grid intersection forced an unresolvable value (such as a prime number resulting from a division, or an operation exceeding the max value boundaries), the generator would stall, drop the map entirely, and tank the frame rate.

The Solution: I refactored the pipeline into an analytical algebraic cascade solver. Instead of guessing values, the algorithm dynamically deduces the exact prime factors and valid divisors for intersecting cells frame-by-frame, completely eliminating generation timeouts and preventing DivideByZeroException edge cases.

**Minimizing Human Error in Hand-Crafted Level Design**

The Problem: Designing complex overlapping math grids by hand inside the standard Unity Inspector was slow, abstract, and highly prone to broken equation chains that ruined the puzzle logic.

The Solution: I developed a permanent, global Scene View overlay window using advanced Editor Scripting ([InitializeOnLoad] and EditorGUI.BeginChangeCheck). The tool forces cell elements into valid coordinates automatically via custom grid snapping and provides instant visual validation, turning invalid or misplaced cells bright red to streamline designer iteration.

#### Key Takeaways

- Deduction Over Randomness: In procedural systems with strict constraints, algorithmic deduction is vastly superior to random brute-force sampling in terms of performance, stability, and rule enforcement.

- Tools Empower Workflow: Investing time into writing custom engine extensions, visual debuggers, and layout constraints early in production saves dozens of hours of manual asset configuration.

- Architectural Decoupling: Keeping MonoBehaviours isolated from core data states makes systems highly reusable, painless to debug, and trivial to serialize into web-ready formats like JSON.

