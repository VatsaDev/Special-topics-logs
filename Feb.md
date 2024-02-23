# Feb Logs

## Week 1
 - looking into RL
    - agent, action, environment, state, reward
    - agent, gives action to env.
    - the state of the env is there, depending on how well it does in the state, gets a reward
    - the goal is to maximize cumulative reward
 - State Space
    - State: complete world info, everything is known
    - observation: part of the overall state
 - Action space
    - Discrete: number of actions is finite
    - continuous: number of actions is infinite
 - Reward and discount
    - set a discount amount gamma, the larger the gamma, the more the agent cares about long term reward
    - short gamma, short term reward
 - Tasks
    - A task is an RL problem instance
    - Episodic task: Have a starting point and end point
    - Continuous Tasks: Are always running, user stops them, agent learns best actions and simultaneously interacts with the environment
 - Exploration v. Exploitation
    - Exploitation only uses the nearest rewards
    - Exploration helps find more rewards
 - The main ways to solve an RL problem
    - Policy, RL brain, the point is to find the optimal policy
       - direct: teach the model an action to take, policy based methods
         - Makes a map of state to action
         - stochastic and deterministic, first one give a probability range, second gives the same value every time
       - indirect: teach the model which state is more valuable, take an action that leads to more valuable states
         - value function, maps state to value, expected value of state
 - Q-learning/DeepQ-learning
    - Q-learning
       - state and action input to Q table
       - get Q value out
    - Deep Q learning
       - state input to deep Q NN
       - Q value actions out

 - Training a simulation
    - box2d environment with gymnasium
    - uses stable baselines 3
    - Uses gymnasium
       - a way to make RL state/environment easy
       - steps
          - create env with `gymnasium.make()`
          - reset env with `observation = env.reset()`
          - get a model action
          - change the env with `env.step(action)`
             - gives the observation (new state), reward, whether we terminated of not, truncated(time-limit/out of bounds)
             - if terminated, we use `observation = env.reset()`
    - Use PPO
       - surprising to see this so early, thought PPO was a more late game technique
       - train this simple model for 1,000,000 time steps (~20 min) for a simple env, more complex ones will take days 
       - Hmm Karpathy made hos own reinforce.js for RL in browser, maybe implement PPO in browser with three.js for environments
       
 - Further reading
    - Deep RL: Pong from pixels
       - The 4 parts of AI
          - Compute(GPUs, ASICs)
          - Datasets
          - algorithms
          - infra (HPC, linux, etc)
       - policy gradients work much better than DQN
       - Pong is a case of MDP, Markov decision process, a graph where every node is state and reward, and all the edges are transitions. Goal is to maximize total reward from transitions
       - learning pong from raw pixels means getting an environment of a pong state, 210x160x3 values, RGB pixel for a 210x160 instance
       - low action space, up/down per paddle, great toy problem
       - the policy network is a 2 layer model
          - Input of 100800 numbers, 210x160x3
          - action is just the probability of going up
          - stochastic sampling of probabilities
       - supervised learning
          - the parameter and gradient changes due to the scenario
          - helps the model predict similar moves in similar scenarios
       - policy gradients
          - helps against bad labels in supervised learning 
          - the outcome of the game determines the probabilities of actions
       - Win/loss to actions
          - If the game is won, its all good actions
          - if the game is lost its all bad actions
          - bad in a couple games, but works out in the long run
       - another possibility is the discount with cumulative earlier

 - Making custom RL environments
    - define state and action space
    - define rewards
    - gym works, but other RL can be better
    - make sure to have resets and steps
    - render is possible with anything, many do it in pygame

 - Reinforcement learning the book
    - RL is unsupervised learning, about finding structure hidden in collections of unlabelled data
    - Exploration v. Exploitation, neither one can happen independently, one has to do both to succeed
    - Limitations and scope
       - RL relies heavily on state (whatever information is available to the model)
       - a lot happens in effectively using state to actions in RL
       - model free arch tend to be stateless, prev situations don't really affect current situation, each situation can be played on its own
    - RL history
       - Trial and error comes from the 1948 pleasure-pain report

 - Huggy the dog RL through HF
    - based off unity ML agents
    - Huggy's state is the stick pos, the relative pos between dog and stick, and leg orientation
    - Huggy learns to rotate his legs
    - the goal in this case is getting to the stick without spinning too much
    - multipart reward function
       - reach target bonus
       - time penalty
       - orientation bonus
       - rotation penalty

 - 3d terrain gen with triangles/polygons
    - useful for future work, thin-matrix equinox style sim
    - start with a sin wave, convert to triangle mesh
    - in 2d, using marching squares, 3d used marching cubes
    - sin waves are unrealistic, use the simplex noise function instead
    - build the noise gen in chunks for performance
    - marching cubes are chunky, add interpolation for smoothness
    - use fractal noise on the fractal noise to make it natural

 - Intro to Q-learning
    - deeper dive to value based methods
    - using Q-learning, two methods
       - policy only, train policy, policy is nn, train the policy directly
       - value based, policy is a function defined, optimal value function, optimal policy
          - train a value-function that is an NN

 - The bellman equation
    - calculating expected rewards
    - sum of the immediate reward and discounted value of following state

 - two learning strats, monte carlo v temporal diff.
    - both are strats on training value/policy function
    - Monte Carlo waits for a complete state, the whole thing, compares actions across
    - Temporal diff updates after each action
    - (I feel like temporal diff would be faster, but not as exploration-based, and therefore have a lower cap) 

 - Intro to Q-learning
    - off policy
    - value based method, find the optimal policy indirectly
    - temp. diff approach, update per step
    - state-action pair values encoded in q-table
    - value and policy linked, the q-table is initially useless, the policy changes that

    - Q-table Algo
       - initialize Q-table, all values 0
       - use epsilon greedy strats to get the action
       - over time exploration drops, exploitation starts
       - perform action, get reward
       - update Q-table
   
    - off policy vs on policy
       - off has diff policy for acting and updating
       - on has same policy for both

 - monte carlo v td
    - Monte Carlo needs more data samples, while TD needs less
    - TD has a huge bias towards initial start, and this can be a problem sometimes
    - (Hmm, The evo sim would need monte carlo, as TD would be very biased to starting env, while evo sim would be really diverse, Raw Pixel RL)

 - feb 7
    - not able to do much today, but did look at DSA, its been a month or so since the google foobar challenge

 - feb 12
    - looked into the function call creation
    - so now that FTC is over, i plan to create a voice to functions that the robot executes
    - theres 17 possible robot states, instructions = ["forward()","backward()","strL()","strR()","spin()","tL()","tR()","diagR()","diagL()","e_out()","e_in()","l_claw(0)","l_claw(1)","r_claw(0)","r_claw(1)","wrist_up()","wrist_down()"]
    - make a random combination dataset of this, limit to about 20 million instructions
    - convert them all to natural language instructions 
    - use stt for get the text i speak, then convert to functions, send to bot

   - on other topics, Deep Q-learning, real RL
   - Q tables just set rewards, but the tables only work for small action/env spaces, while larger ones are impossible to make that way

   - setting up a vllm endpoint for phi-2
   - speedy high tok/s counts to convert instructions

 - Feb 21, been awhile since I updated, but was looking into a lot of diverse topics
    - started looking at a curriculum learning paper, about feeding ai data in an increasingly difficult rate
    - Lilith the optimizer, testing it out
    - Data generation with the function calling

 - Feb 23
    - start PicoCTF challenges, working through them to learn cybersecurity, fun puzzles
    - Looking into deep-Q learning, analyzing structure
       - For Atari
          - takes 4 images at a time, processes them with convolutional layers, to downsize and grayscale
          - Then takes these values, gets fully connected layers to pick probabilities
          - 4 frames at a time, as one frame is not enough to figure out temporal stuff, predict whats next