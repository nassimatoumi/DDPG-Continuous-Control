# DDPG-Continuous-Control

## Description

In this project, a DDPG agent is trained to control a double-jointed arm in order to move it to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location for as many time steps as possible, to maximize the cumulated reward.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The task is episodic, and the agent is trained once the average score has reached +30 for over 100 consecutive episodes.

For this project, two separate versions of the Unity environment can be used to train the model:
- The first version contains a single agent.
- The second version contains 20 identical agents that share the same model, each with its own copy of the environment. In this case, the score for each episode is computed by averaging over the scores of the 20 agents.

In this repository, the environment is solved using the second version.

### Getting Started: 
To run this project, multiple dependencies should be met. In particular, the environment should be installed. 

Depending on the host operating system, the environment can be downloaded from one of the following links:
- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Windows_x86_64.zip)
    
Afterwards, the file should be decompressed, and the path for the environment file should be edited on the **train_agent.py** and **use_agent.py** files, at line 9. 

### Instructions:
- To train the agent from scratch, run the following command, while specifying in the file the path of the newly created model if needed:

    **python3 train_agent.py**

Note that the hyperparameter values can be tuned in the dqn_agent file, and the Deep Neural Network architecture can be changed in the file model.py 

- To use the trained model, run the following command:

    **python3 use_agent.py**
    
The path of the actor and critic model files can be specified in lines 38 and 39. 
