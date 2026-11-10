# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process


## Aim
To represent a robot waiter in a restaurant as a Markov Decision Process (MDP) by defining its states, actions, transition probabilities, reward function, and Python representation for efficient customer service.



## Problem Statement
A robot waiter works in a restaurant by taking customer orders, collecting food from the kitchen, delivering it to the correct table, and returning for the next order. The robot must navigate safely while avoiding obstacles such as customers, chairs, and other staff. At each step, it decides whether to move, pick up food, deliver food, or return to the kitchen. It receives positive rewards for successful deliveries and customer satisfaction, while collisions, delays, and wrong deliveries result in negative rewards.

### Problem Description
A restaurant robot waiter assists customers by autonomously delivering food from the kitchen to dining tables. The robot observes its current state, chooses an appropriate action, and moves through the restaurant while avoiding obstacles. It earns rewards for timely and correct deliveries and receives penalties for collisions, delays, or incorrect deliveries. The objective is to determine the optimal sequence of actions that maximizes customer satisfaction and restaurant efficiency.

Describe the real-world application that you selected.


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
The state space lists all possible situations in which the agent can exist.
```
S = {

S1 = Robot Waiting

S2 = Order Received

S3 = Moving to Kitchen

S4 = Food Picked Up

S5 = Moving to Customer Table

S6 = Obstacle Detected

S7 = Food Delivered

S8 = Wrong Delivery

S9 = Returning to Kitchen

S10 = Task Completed (Goal State)

}
```



---

## Sample State


A sample state is one specific example from the state space.
```
S4 = Food Picked Up
```
This means the robot has collected the customer's food from the kitchen and is moving toward the assigned table.



---

## Action Space

The action space should lists all possible actions available to the agent.

```
A = {

Receive Order

Move Forward

Turn Left

Turn Right

Pick Up Food

Deliver Food

Avoid Obstacle

Return to Kitchen

}
```




---

## Sample Action


A sample action is one action selected from the action space.

```
Deliver Food
```
The robot serves the food to the correct customer.



---

## Transition Probability




The transition probability specifies the probability of moving from one state to another after taking an action.

General form:

$$
P(s' \mid s,a)
$$

| Current State | Action | Next State | Probability |
|--------------|--------|------------|------------:|
| Order Received | Move to Kitchen | Food Picked Up | 0.95 |
| Food Picked Up | Deliver Food | Food Delivered | 0.90 |
| Moving to Customer Table | Avoid Obstacle | Moving to Customer Table | 0.85 |
| Moving to Customer Table | Move Forward | Wrong Delivery | 0.10 |

**Meaning:**

- There is a **95%** chance that the robot successfully reaches the kitchen after receiving an order.
- There is a **90%** chance that the robot delivers the food successfully.
- There is an **85%** chance that the robot avoids an obstacle and continues moving.
- There is a **10%** chance that the robot delivers the food to the wrong table or makes a navigation error.
## Reward Function


The reward function defines the feedback received by the agent after taking an action.

General form:

$$
R(s,a,s')
$$

| Situation | Reward |
|-----------|--------|
| Successful Delivery | +100 |
| Correct Food Pickup | +20 |
| Every Movement | -1 |
| Obstacle Collision | -30 |
| Wrong Delivery | -50 |
| Task Completed | +150 |

**Example:**

| Action/Event | Reward |
|--------------|--------|
| Successful Delivery | +100 |
| Move One Step | -1 |
| Obstacle Collision | -30 |
| Wrong Delivery | -50 |
| Task Completed | +150 |


---

## Graphical Representation

<img width="1535" height="1024" alt="GRAPH" src="https://github.com/user-attachments/assets/350227c5-4215-40d8-8e0b-5ec9edb96fbe" />



---

## Program




```
# MDP Representation using Python
print("Name : Kanigavel M")
print("Register Number : 212224240070")

states = [
    "Robot Waiting",
    "Order Received",
    "Moving to Kitchen",
    "Food Picked Up",
    "Moving to Customer Table",
    "Obstacle Detected",
    "Food Delivered",
    "Wrong Delivery",
    "Returning to Kitchen",
    "Task Completed"
]

actions = [
    "Receive Order",
    "Move Forward",
    "Turn Left",
    "Turn Right",
    "Pick Up Food",
    "Deliver Food",
    "Avoid Obstacle",
    "Return to Kitchen"
]

transition_probability = {

("Order Received","Move to Kitchen"):{
"Food Picked Up":0.95,
"Obstacle Detected":0.05
},

("Food Picked Up","Deliver Food"):{
"Food Delivered":0.90,
"Wrong Delivery":0.10
},

("Food Delivered","Return to Kitchen"):{
"Task Completed":1.0
}

}

reward = {

"Food Pickup":20,
"Successful Delivery":100,
"Move":-1,
"Obstacle Collision":-30,
"Wrong Delivery":-50,
"Task Completed":150

}

discount_factor = 0.9

print("\nStates")
print(states)

print("\nActions")
print(actions)

print("\nTransition Probability")
for key,value in transition_probability.items():
    print(key,"->",value)

print("\nReward Function")
for key,value in reward.items():
    print(key,":",value)

print("\nDiscount Factor =",discount_factor)

```
---
## Output
<img width="1421" height="341" alt="image" src="https://github.com/user-attachments/assets/38fe213d-6845-48c9-ab41-3a9cb3a52e4a" />



---

## Result

Thus, the robot waiter in a restaurant was successfully represented as a Markov Decision Process (MDP) by defining its state space, action space, transition probability function, reward function, discount factor, graphical representation, and Python implementation.



---

