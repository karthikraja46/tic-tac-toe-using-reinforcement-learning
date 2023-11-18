# Tic-Tac-Toe with Reinforcement Learning

The directory `tictactoe` contains the core source code for this project.
There are 3 main source code files:
1. game.py
2. agent.py
3. teacher.py

I have implemented two RL agents that learn to play the game of tic-tac-toe:
one follows the SARSA algorithm, and the other follows Q-learning.
These agents are trained by a teacher agent that knows the optimal strategy;
To initialize the learning agent Q values,
I make use of default dictionaries with default values of 0 such that the
value for every state-action pair is initialized to 0.

The Q-learning and SARSA agents are implemented in `agent.py`.
Each of the two learning agents inherit from a parent learner class; the key difference between the two is their Q-value update function. 

The Teacher agent is implemented in `teacher.py`. 
The teacher knows the optimal policy for each state presented; however, this agent only takes the optimal choice with a set probability.

In `game.py`, the main game class is found. 
The Game class holds the state of each particular game instance, and it contains the majority of the main game functionality. 
The main game loop can be found in the class's function playGame().

#### Game Script

To play the game (see "Running the Program" below for instructions) you will use the script called `play.py`.
The GameLearner class holds the state of the current game sequence, which will continue until the player choses to stop or the teacher has finished the designated number of episodes.

## Steps to run this program


#### Train a new agent manually
To initialize a new agent and begin a game loop, simply run:

    python3 play.py -a q                (Q-learner)
    python3 play.py -a s                (Sarsa-learner)


    python3 play.py -a q -p my_agent_path.pkl


When unspecified, the path is set to either "q_agent.pkl" or "sarsa_agent.pkl" depending on agent type. If the file already exists, you'll be asked to overwrite.

#### Train a new agent automatically via teacher
To initialize a new RL agent and train it automatically with a teacher agent, use the flag `-t`

    python3 play.py -a q -t 5000

#### Load an existing agent and continue training
To load an existing agent and continue training, use the `-l` flag:

    python3 play.py -a q -l             
    python3 play.py -a q -l -t 5000     



