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
Desired stock level reached	                    +25
Excess inventory	                            -20
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
# States
states = {
    "S1": "Low_Stock",
    "S2": "Medium_Stock",
    "S3": "High_Stock",
    "S4": "Out_Of_Stock"
}

# Actions
actions = {
    "A1": "No_Order",
    "A2": "Small_Order",
    "A3": "Large_Order",
    "A4": "Emergency_Order"
}

# Transition Probabilities P(s' | s, a)
transition_probabilities = {
    ("Low_Stock", "No_Order"): {
        "Low_Stock": 0.3,
        "Out_Of_Stock": 0.7
    },
    ("Low_Stock", "Small_Order"): {
        "Medium_Stock": 0.8,
        "Low_Stock": 0.2
    },
    ("Low_Stock", "Large_Order"): {
        "Medium_Stock": 0.4,
        "High_Stock": 0.6
    },
    ("Low_Stock", "Emergency_Order"): {
        "High_Stock": 0.8,
        "Medium_Stock": 0.2
    },
    ("Medium_Stock", "No_Order"): {
        "Low_Stock": 0.6,
        "Medium_Stock": 0.4
    },
    ("Medium_Stock", "Small_Order"): {
        "Medium_Stock": 0.4,
        "High_Stock": 0.6
    },
    ("Medium_Stock", "Large_Order"): {
        "Medium_Stock": 0.2,
        "High_Stock": 0.8
    },
    ("Medium_Stock", "Emergency_Order"): {
        "Medium_Stock": 0.1,
        "High_Stock": 0.9
    },
    ("High_Stock", "No_Order"): {
        "Medium_Stock": 0.7,
        "High_Stock": 0.3
    },
    ("High_Stock", "Small_Order"): {
        "Medium_Stock": 0.3,
        "High_Stock": 0.7
    },
    ("High_Stock", "Large_Order"): {
        "Medium_Stock": 0.1,
        "High_Stock": 0.9
    },
    ("High_Stock", "Emergency_Order"): {
        "Medium_Stock": 0.05,
        "High_Stock": 0.95
    },
    ("Out_Of_Stock", "No_Order"): {
        "Out_Of_Stock": 1.0
    },
    ("Out_Of_Stock", "Small_Order"): {
        "Low_Stock": 0.8,
        "Out_Of_Stock": 0.2
    },
    ("Out_Of_Stock", "Large_Order"): {
        "Medium_Stock": 0.7,
        "Low_Stock": 0.3
    },
    ("Out_Of_Stock", "Emergency_Order"): {
        "Medium_Stock": 0.4,
        "High_Stock": 0.6
    }
}

# Reward Function R(s, a, s')
rewards = {
    ("Low_Stock", "Small_Order", "Medium_Stock"): 25,
    ("Medium_Stock", "No_Order", "Low_Stock"): -40,
    ("Medium_Stock", "Small_Order", "High_Stock"): 25,
    ("High_Stock", "No_Order", "High_Stock"): 15,
    ("High_Stock", "Large_Order", "High_Stock"): -20,
    ("Out_Of_Stock", "Emergency_Order", "High_Stock"): 50
}

# Discount Factor
mdp = {
    "States": states,
    "Actions": actions,
    "Transition_Probabilities": transition_probabilities,
    "Rewards": rewards,
    "Discount_Factor": 0.90
}

print("\nMDP Representation\n")

for key, value in mdp.items():
    print(f"{key}:")
    print(value)
    print()

# Check transition probabilities
for key, value in transition_probabilities.items():
    print(key, "=", sum(value.values()))
```
---
## Output
<img width="1790" height="620" alt="image" src="https://github.com/user-attachments/assets/371f54c6-2bc7-474a-b116-9062a8b57cf8" />



---

## Result
The Inventory Management System was successfully represented as a Markov Decision Process by defining its states, actions, transition probabilities, reward function, and discount factor.

---

