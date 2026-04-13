# 📦 Big Tech Code Refactoring & Modularization Guide

## Overview
Widely adopted refactoring and modularization principles for large-scale systems. Designed as an **agent skill / engineering guideline**.

---

## 1. Core Refactoring Principles

### 1.1 Single Responsibility Principle (SRP)
- Each function/class does **one thing**
- If description includes “and” → split it

### 1.2 Keep Units Small
- Function: **20–50 lines**
- Class: **single concept**

### 1.3 Clear Interfaces
- Expose **what**, hide **how**
- Avoid leaking implementation details

### 1.4 Minimize Side Effects
- Prefer **pure functions**
- Isolate state mutations

---

## 2. Modularization Rules

### 2.1 Layered Architecture
```
# Example:
/core        # business logic (pure)
/service     # orchestration
/infra       # DB, APIs, external systems
/interface   # REST, CLI, UI
```
- Dependencies flow **top → down only**
- `/core` must not depend on other layers

### 2.2 Dependency Direction
- High-level modules should NOT depend on low-level modules
- Use **interfaces / abstractions**

### 2.3 Module Boundaries
- Use **public APIs only**
- Avoid internal imports

### 2.4 Reusability Rule
- Extract if:
  - Used **2+ times**
  - Logically independent

---

## 3. Refactoring Patterns

### 3.1 Extract Function
```python
# Before
def process():
    a = ...
    b = ...
    c = complex_logic(a, b)

# After
def process():
    c = compute_feature(a, b)
```

### 3.2 Extract Class
- Split multi-responsibility classes

### 3.3 Replace Conditional with Polymorphism
```python
# Bad
if type == "A":
    ...
elif type == "B":
    ...

# Good
class AHandler:
    ...
class BHandler:
    ...
```

### 3.4 Move Logic Closer to Data
- Encapsulate logic near data

---

## 4. Naming Conventions

### Functions
- Verb + Object
  - `get_user()`
  - `calculate_loss()`

### Variables
- Clear and meaningful
- Avoid: `x`, `tmp`, `data`

---

## 5. Code Review

### Key Questions
- Readable?
- Testable?
- Extensible?
- Understandable quickly?

> Code should be understandable after 6 months

---

## 6. Test-Driven Refactoring
```
1. Add tests
2. Refactor
3. Ensure tests pass
```
- Never refactor without validation

---

## 7. Style & Consistency

### Enforced
- Linting
- Auto-formatting
- Strict imports