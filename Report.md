# Report

## Implementation
In this implementation, the DDPG main and target networks for the actor and critic are implemented using PyTorch. 

The neural networks for the actor and critic comprised a batch normalization layer after the input layer, and two hidden layers of 128 and 256 units respectively, with ReLu activation functions, and the activation function of the last layer for the actor being the hyperbolic tangent function (tanh) to get an output between 1 and -1. For each action, the Ornstein Uhlenbeck process is employed to generate noise that is added to encourage exploration.

The solution implements experience replay, to break correlation between the experiences, and thus avoid bias during learning, the experiences are stored in a buffer of a size of 1000000, and randomly sampled in batches of 128.

The neural network weights are updated using the ADAM optimizer, with a learning rate of 1e-4 for the actor, and 1e-3 for the critic, and a discount factor gamma of 0.95. Finally, the learning is performed 5 times using different samples every 20 steps, and the target networks are updated with a soft update using a tau value of 1e-3.

Note that to stabilize learning, the rewards returned by the environment are multiplied by a factor of 0.1. 
## Results
The model was trained on a GPU, and was able to obtain an average reward over the 20 agents of over 30 for 100 consecutive episodes after 127 episodes, as shown in the figure below.

![alt text](https://github.com/nassimatoumi/DDPG-Continuous-Control/blob/d43202de07b882d4c65590dbbf268d01f7328995/Scores.png)

The saved weights can be found in the files **critic_checkpoint.pth** and **actor_checkpoint.pth** 

## Future works
Although the agent was able to reach the target score, multiple enhancements might be considered for future works to improve its performance:
- Prioritized Experience Replay, which should allow the model to converge more quickly by reusing experiences that the model learns from the most (biggest TD error). 

- Other methods such as TD3 (Twin Delayed DDPG) could be explored for a more stable learning.

- Deeper neural networks might also improve the obtained results.
