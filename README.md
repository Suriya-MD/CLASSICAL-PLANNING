# ExpNo:10 Implementation of Classical Planning Algorithm
### Name: SURIYA M
### Reference Number: 212223110055
# Algorithm or Steps Involved:
<ol>
  <li>Define the initial state</li>
  <li>Define the goal state</li>
  <li>Define the actions</li>
  <li>Find a <b>plan</b> to reach the goal state</li>
  <li>Print the plan</li>
</ol>

# Example - 1
```
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_Table': {'precondition': {'A': 'Table', 'B': 'B'}, 'effect': {'B': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B']
```
# Example - 2
```
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_C': {'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'}, 'effect': {'B': 'C'}},
    'move_C_to_Table': {'precondition': {'A': 'B', 'B': 'C', 'C': 'C'}, 'effect': {'C': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B', 'move_B_to_C']
```

# Please Prepare Solution or Definition For the method find_plan(initial_state, goal_state, actions)
<h3>You Can use any of the searching Strategies for planning and executing a sequence of actions.<br> You can also look in to the Code given in the Repository.</h3>

# Program:
```
def is_goal_state(current_state, goal_state):
    return current_state == goal_state
def apply_action(current_state, action_effect):
    new_state = current_state.copy()
    new_state.update(action_effect)
    return new_state
def find_plan(initial_state, goal_state, actions):
    queue = [(initial_state, [])]
    visited_states = set()
    while queue:
        current_state, partial_plan = queue.pop(0)
        if is_goal_state(current_state, goal_state):
            return partial_plan
        if tuple(current_state.items()) in visited_states:
            continue
        visited_states.add(tuple(current_state.items()))
        for action in actions:
            if is_applicable(current_state, actions[action]['precondition']):
                next_state = apply_action(current_state, actions[action]['effect'])
                queue.append((next_state, partial_plan + [action]))
    print("No plan exists.")
    return None
def is_applicable(current_state, precondition):
    return all(current_state.get(key) == value for key, value in precondition.items())
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}
actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_Table': {'precondition': {'A': 'Table', 'B': 'B'}, 'effect': {'B': 'Table'}}
}
plan = find_plan(initial_state, goal_state, actions)
print(plan)
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}
actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_C': {'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'}, 'effect': {'B': 'C'}},
    'move_C_to_Table': {'precondition': {'A': 'B', 'B': 'C', 'C': 'C'}, 'effect': {'C': 'Table'}}
}
plan = find_plan(initial_state, goal_state, actions)
print(plan)
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'Table', 'B': 'Table'}
actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}}
}
plan = find_plan(initial_state, goal_state, actions)
print(plan)
```

# Output:

![image](https://github.com/user-attachments/assets/6db5a14b-d1ef-4b75-a56d-22eb879f3f3e)

![image](https://github.com/user-attachments/assets/52b89c27-df71-4cbb-9fe7-ef8954b42311)


# Result:
Thus Program for Implementation of Classical Planning Algorithm was executed Successfully.
