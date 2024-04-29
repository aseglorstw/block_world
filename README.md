## Block World solution with Q-Learning
We have a worker named Henwas who moves blocks around, following a certain sequence. However, he's become a bit forgetful and needs guidance. Additionally, sometimes blocks might end up in places he didn't expect. Your task is to write a policy for Henwas so that he can move blocks correctly despite random errors.

### Solution with Q-Learning
To solve this task, we use the Q-Learning algorithm. Q-Learning is a fundamental reinforcement learning algorithm that learns through interactions with the environment, evaluating actions based on the rewards received. Our goal is to minimize Henwas' mistakes and maximize his productivity.

#### Step-by-Step Solution
1. **Environment Initialization**: We use the `BlockWorldEnv` class, which allows us to create various block states and generate available actions.

2. **Creating the Q-Table**: The Q-table holds Q-values for each state-action pair. It is updated based on the experience gained during training. We use a dictionary to store Q-values.

3. **Training**: Initially, set up some variables, including learning parameters like `alpha` (learning rate), `gamma` (discount factor), and `epsilon` (for `ε-greedy`). Then:
   * Use the `reset()` method to start a new episode and get the initial state.
   * Use the `step(a)` method to perform action `a`, getting a new state, reward, and a completion status (`done`).
   * Update Q-values using the Q-Learning update rule:
     $$ Q(s, a) = (1 - \alpha) \times Q(s, a) + \alpha \times (r + \gamma \times \max(Q(s', a'))) $$
   * Repeat these steps until the completion condition is met.

4. **Action Selection (Policy)**: After training, use the `act(s)` method to select an action based on the current state. We choose the action with the highest Q-value, but also consider the `epsilon` factor to occasionally select random actions, allowing exploration of possible alternatives.

Thus, we create a policy that can adapt to changes in the environment, ensuring Henwas performs the correct actions to successfully move blocks.
