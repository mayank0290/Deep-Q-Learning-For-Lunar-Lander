
## Project Overview

This project implements a Deep Q-Network (DQN) reinforcement learning agent to solve OpenAI Gymnasium's Lunar Lander environment. The agent learns to control a spacecraft to land safely on a landing pad on the lunar surface.

## Environment Description

In this environment, the agent controls a lunar lander with four actions:

*Do nothing*

*Fire left thruster*

*Fire main thruster*

*Fire right thruster*

The state space consists of 8 variables:

Coordinates (x, y)
Linear velocities (x, y)
Angle
Angular velocity
Two booleans indicating if each leg is in contact with the ground

**Rewards are given for:**

*Moving toward the landing pad*

*Coming to rest on the landing pad*

*Using minimal fuel*

*Crashing results in negative rewards*

## Implementation Details
### Neural Network Architecture

The agent uses a simple neural network with:

* Input layer (state size)
* Two hidden layers (64 units each with ReLU activation)
* Output layer (action size)

### Key Reinforcement Learning Components

* Experience Replay: Stores experiences in a replay buffer to break correlations between consecutive samples
* Fixed Q-Targets: Uses two networks (local and target) to stabilize learning
* Soft Updates: Gradually updates target network parameters
* Epsilon-Greedy Exploration: Balances exploration vs. exploitation with decaying epsilon

## Hyperparameters
```
Learning Rate: 5e-4

Minibatch Size: 100

Discount Factor: 0.99

Replay Buffer Size: 1e5

Tau (for soft updates): 1e-3

Epsilon Start: 1.0

Epsilon End: 0.01

Epsilon Decay: 0.995
```
## Training Process
The agent is trained for up to 2000 episodes, with each episode limited to 1000 timesteps. The environment is considered solved when the agent achieves an average score of at least 200 over 100 consecutive episodes.
During training:

* Epsilon gradually decays from 1.0 to 0.01
* Performance is tracked using a running average of the last 100 episodes
* The model is saved once the environment is solved


## Requirements
```
gymnasium
torch
numpy
matplotlib
imageio
```
## Installation

#### Install gym and necessary dependencies
```
pip install gymnasium
pip install "gymnasium[atari, accept-rom-license]"
apt-get install -y swig
pip install gymnasium[box2d]
```
Other requirements

pip install torch numpy matplotlib imageio

## Usage
```
python train.py
```
> Watch trained agent
```
python evaluate.py
```
##File Structure
```
dqn_agent.py: Contains the Agent and ReplayMemory classes
model.py: Defines the neural network architecture (Brain)
train.py: Script for training the agent
evaluate.py: Script for watching the trained agent
checkpoint.pth: Saved model weights after successful training
```
## Visualization
The project includes code to create and display videos of the trained agent's performance using imageio and IPython's HTML display capabilities.

## Acknowledgements

OpenAI Gymnasium for the Lunar Lander environment