# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process
## Aim
To model an Inventory Management System using a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, rewards, and Python representation.

---

## Problem Statement

### Problem Description

An inventory management system monitors stock levels and decides when and how much stock to order. The objective is to maintain sufficient stock, avoid shortages, and reduce excess inventory and ordering costs.

---

## MDP Components

A Markov Decision Process is represented as:

$$
MDP = (S, A, P, R, \gamma)
$$

Where:

| Symbol | Meaning |
|---|---|
| $S$ | Set of states |
| $A$ | Set of actions |
| $P$ | Transition probability function |
| $R$ | Reward function |
| $\gamma$ | Discount factor |

---

## State Space

The state space lists all possible inventory conditions.

```
S = {
    Low_Stock,
    Medium_Stock,
    High_Stock,
    Out_Of_Stock
}
```
---

## Sample State
A sample state is one specific example from the state space.
```
Low_Stock
```
---

## Action Space

The action space lists all possible actions available to the agent.
```
A = {
    No_Order,
    Small_Order,
    Large_Order,
    Emergency_Order
}
```


---

## Sample Action
A sample action is one action selected from the action space.
```
Small_Order
```
---

## Transition Probability

Transition probability explains how the stock level changes after an action is taken.

General form:

$$
P(s' \mid s,a)
$$

```
From Low_Stock, after Small_Order:
Medium_Stock = 0.80
Low_Stock = 0.20

From Medium_Stock, after No_Order:
Low_Stock = 0.60
Medium_Stock = 0.40

From Out_Of_Stock, after Emergency_Order:
High_Stock = 0.60
Medium_Stock = 0.40
```

---

## Reward Function

The reward function defines the feedback received by the agent after taking an action.

General form:

$$
R(s,a,s')
$$

```
Situation	                                Reward

Stock maintained at a suitable level            +50
Ordering cost reduced                           +15
Desired stock level reached	                  +25
Excess inventory	                          -20
Stock shortage                       	        -40
```
---
## Discount Factor

γ = 0.90

## Graphical Representation

<img width="1536" height="1024" alt="Inventory Management MDP Diagram" src="https://github.com/user-attachments/assets/a21fe0ae-4649-4faa-89c0-e11965ab3b17" />

---

## Python Representation

### MDP Representation using Python
### Name : RAMESH RENUKA
### Register Number : 212223240136

```

from pprint import pprint

# State mapping
states = {
    0: "Low_Stock",
    1: "Medium_Stock",
    2: "High_Stock",
    3: "Out_Of_Stock"
}

# Action mapping
actions = {
    0: "No_Order",
    1: "Small_Order",
    2: "Large_Order",
    3: "Emergency_Order"
}

# MDP Transition Representation
P = {
    0: {
        0: [(0.3, 0, 0, False), (0.7, 3, 0, False)],
        1: [(0.8, 1, 25, False), (0.2, 0, 0, False)],
        2: [(0.4, 1, 0, False), (0.6, 2, 0, False)],
        3: [(0.8, 2, 0, False), (0.2, 1, 0, False)]
    },

    1: {
        0: [(0.6, 0, -40, False), (0.4, 1, 0, False)],
        1: [(0.4, 1, 0, False), (0.6, 2, 25, False)],
        2: [(0.2, 1, 0, False), (0.8, 2, 0, False)],
        3: [(0.1, 1, 0, False), (0.9, 2, 0, False)]
    },

    2: {
        0: [(0.7, 1, 0, False), (0.3, 2, 15, False)],
        1: [(0.3, 1, 0, False), (0.7, 2, 0, False)],
        2: [(0.1, 1, 0, False), (0.9, 2, -20, False)],
        3: [(0.05, 1, 0, False), (0.95, 2, 0, False)]
    },

    3: {
        0: [(1.0, 3, 0, False)],
        1: [(0.8, 0, 0, False), (0.2, 3, 0, False)],
        2: [(0.7, 1, 0, False), (0.3, 0, 0, False)],
        3: [(0.4, 1, 0, False), (0.6, 2, 50, False)]
    }
}

print("MDP Representation")
print("\nStates:")
print(states)

print("\nActions:")
print(actions)

print("\nTransition Probability P:")
pprint(P, sort_dicts=False, width=80)

```
---
## Output
<img width="677" height="461" alt="image" src="https://github.com/user-attachments/assets/1a51f996-a8ea-44e5-8719-7e445b265922" />



---

## Result
The Inventory Management System was successfully represented as a Markov Decision Process by defining its states, actions, transition probabilities, reward function, and discount factor.

---

