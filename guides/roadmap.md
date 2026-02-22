# 🧠 Concepts to learn

**learn quant + systems simultaneously**, not as theory.

## Phase 0 — Service foundations

Engineering concepts:

* REST microservice design in C++
* serialization (JSON ↔ domain models)
* CMake for production builds
* dependency management
* Dockerising C++ services

Outcome:
A deployable service.

---

## Phase 1 — Lending math (practical quant)

Implement:

* amortization schedules
* principal vs interest breakdown
* compounding
* annuities

Concepts learned:

| Concept             | Why it matters       |
| ------------------- | -------------------- |
| Time value of money | Core of lending      |
| Discounting         | Pricing loans        |
| Compounding         | Interest mechanics   |
| Cash flows          | What QuantLib models |


---

## Phase 2 — QuantLib fundamentals

Learn the real primitives:

* Dates & calendars
* Day count conventions
* Term structures
* Yield curves
* Cashflow modelling

These are the backbone of:

* banking
* treasury
* risk

---

## Phase 3 — Pricing engine thinking

Move from “calculator” → “pricing system”.

Concepts:

* deterministic pricing
* input → model → output pipelines
* instrument modelling
* reusable pricing engines

Make it **bank-grade**.

---

## Phase 4 — Risk & sensitivity

Add:

* rate shocks
* payment sensitivity
* interest exposure
* scenario simulation

Concepts:

| Concept        | Industry name    |
| -------------- | ---------------- |
| change in rate | DV01 thinking    |
| payment change | sensitivity      |
| total exposure | duration mindset |

Thinking like treasury/risk.

---

## Phase 5 — Architecture thinking

Design as:

* stateless service
* horizontally scalable
* pricing as a platform

Concepts:

* separation of core ledger vs pricing engine
* event-driven recalculation
* service boundaries

---

# 💼 Why am I not doing this in C#?

Yes — I *can* do this in C#.

But here’s the reasoning for choosing C++.

## 🧩 Reason 1 — QuantLib is native C++

QuantLib:

* written in C++
* designed for performance
* direct bindings

C# options:

* wrappers
* interop
* performance overhead

If pricing is critical:

> go native.

---

## 🧩 Reason 2 — Deterministic performance

Pricing engines need:

* predictable latency
* high throughput
* tight memory control

C++ gives:

* zero GC pauses
* deterministic memory
* better parallelism control

In risk/pricing systems:
this matters a lot.

---

## 🧩 Reason 3 — Industry reality

In finance:

| Area                    | Typical language |
| ----------------------- | ---------------- |
| trading/pricing engines | C++              |
| risk engines            | C++              |
| execution systems       | C++              |
| retail backend          | Java/C#          |
| orchestration APIs      | Java/C#          |

Service becomes:

```
.NET services → call → C++ pricing engine
```

This is extremely common.

---

## 🧩 Reason 4 — Separation of responsibilities

I'm not replacing C#.

I'm introducing:

> **a compute engine**

C#:

* orchestration
* APIs
* product logic

C++:

* math
* pricing
* simulation
* risk

---

## 🧩 Reason 5 — Resume & credibility impact

A C# pricing service:

* “backend”

A C++ QuantLib service:

* “quant systems”
* “high-performance computing”

---

# 🧠 Approach justification

> “We keep product logic in .NET, but isolate pricing and risk into a high-performance compute service using C++ and QuantLib.”

Benefits:

* faster calculations
* reusable pricing engine
* independent deployment
* future-ready for complex products

---

# 🏗️ What we’re ACTUALLY building

Not a calculator.

We’re building:

## Lending Pricing Engine

Capabilities:

* loan pricing
* repayment simulation
* interest risk
* yield curves

Interface:

```
POST /loan/price
POST /loan/schedule
POST /loan/risk
POST /rates/curve
```

---

# 🚀 The feature

We will include:

## Scenario simulation

Example:

> “What happens if rates rise 1%?”

> “What if customer prepays in year 5?”

> “What if loan refinances?”

Now I’ve built:

* a product tool
* a risk tool
* a treasury tool

---

# 🧭 The learning curve

Week 1:

* C++ service
* REST
* amortization math

Week 2:

* QuantLib basics
* loan modelling

Week 3:

* risk scenarios
* curve modelling

Week 4:

* production polish

Goal:
Understand more finance.

---

# 🔥 Next step: start building

We begin with:

## Step 1

Project scaffold:

* CMake
* REST framework
* QuantLib integration

## Step 2

First endpoint:

```
POST /loan/price
```

## Step 3

First quant model:

* amortized loan

---

Before I generate the starter code, one critical technical choice:

### REST framework for C++

Tech Stack choice: Drogon
