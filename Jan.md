# January Logs

# Week 1
 - Goal: Cellular Automata, Conway's game of life
 - Interesting algorithm, but no real world use cases that I know of, beyond terraria and other simulations
 - Could it used by some Cybersecurity Neighboring device issues or something?
 - Used In a Minecraft Simulation once, was really powerful at state tracking/mimicking natural processes

# Week 2
 - Goal: Look into how genetic algorithms work
 - Basic Principals, Reranking and Crossover and Mutation
    - Reranking
        - Scoring all instances on a fitness function, who did the best
        - Fitness function, The scoring
     - Crossover
         - Combining the traits of two instances to form a new instance
     - Mutation
        - changing a couple values randomly to represent entropy and nature
# Week 3
 - Goal: being able to use A classification model
 - Found ML5.js, appears to have a useable classification model
 - appears to work well with two inputs/outputs, successfully becomes a Pro at the Dino game

# Week 4  
 - Goal: Putting all the principles so far together and making a useable genetic algorithm demo
 - A Game engine is overkill for this, and canvas is too low level, settled for P5.js
 - Fiddled with it a little bit, simulation and clones work
 - Added ML5.js work, now the classification is possible, but poor for the number of inputs and outputs
 - Reranking is possible between the foxes and chickens with the score for chickens being who lived, and the score for foxes being the chickens eaten
 - Crossover is possible with ML5.js
 - It works, but their brains suck, will use Feb start to make a proper synth data CNN, and custom crossover
 - started working on data loader, but need a way to transmit data to a file, probably going for 800k-1M samples for a proper dataset
 - Last day of Jan, trained the CNN, MLP, and bigram, like a month ahead of schedule
 - started looking into RL