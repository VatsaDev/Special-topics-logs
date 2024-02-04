# Thin matrix equinox

## RL agent animals
 - Fish (Salmon, etc) (good initial, also water test)
 - sheep (social behavior test)
 - falcon (flight and tree nesting env.)
 - penguin (ice/slippery env. test)
 - rabbit (good first model.)
 - peacock (test, better model, different behaviors)
 - camel (new env.)
 - wolves (pack behavior tests)
 - hyena (scavenger work?)

## RL test environments
 - grasslands (rabbit, wolf, sheep, dynamics)
 - light forestry (Multiple predator/prey birds, falcon, flight, etc)
 - river to shallow reef to deep ocean (fish, saltwater/freshwater requirements, pressure requirements, predators, Raw pixel learning, teaching camouflage?)
 - desert/polar (low resource env, exploration v. exploitation tradeoffs)
 - jungle (Very, very dense on species (frogs, boars, eagles, monkeys, etc), tree/vine env. more functionality, complex state, lots of interactions to see)

## props
 - trees (regular, pine, etc)
 - fruits/veggies, apples, carrots, etc (RL food reward)
 - grass
 - flowers
 - boulders
 - bamboo
 
## Terrain
 - low poly mode, simplex noise, marching cubes design and stuff
 - trees/animals are all models
 - (Hmm if designing in js use 3.js as backbone?)
 - plants affect the biome around them
 - small pebbles, fruit drops, etc, that RL agents can interact with
 - plants use genetic algorithms, animals use RL
 - gradually change color to biome, pick an initial color, and interpolate between colors for surrounding vertices
 - RL reproduction is a milestone, rewards per animal

 - boulders, sand, coral/seaweed, underwater
 - Making water
     - start with a flat plain of triangle mesh, square at sea level
     - update heights dynamically on GPU for water moving effect
     - randomized sin waves to create ripples
     - add diffuse, specular lighting to the water
     - add reflection and refraction, and the fresnel effect
     - add a bit of blur to make deeper areas murkier
     - add soft edges where it touches the land
 - have lighting and shadows, RTX ray tracing
 - had to deal with java for UI, but i can have html/css ui

 - post-processing, vfx (hmm, possible in 3.js?)
     - depth of field effect, gauss blur areas depending on the dist from the camera 
     - bloom effect, brightest parts of the scene look like they actually glow, done by increasing the brightness and gaussian blurring areas
     - make the world edges blur out, surround the island with ocean 

 - growing mechanic, certain trees grow out over time, multiple stages

 - the volume of each animals sounds have defaults, but it increases depending on how close you are to the sound, spatial audio, the audio comes from a direction
 - ambient sounds, birds tweeting, grass shuffling, wind, etc, per biome
 - overall background music systems playing a soundtrack

 - weather with particle effects, snowfall, rain, etc
 - local weather

 - world saves
     - save the evo state, procedural generation with seed, store seed for world gen
     - store all entity info, (any animals, props, etc)
     - store all the RL networks?

 - entities can be different colors, multicolor trees, multicolor animals
 - change the models colors on brightness
 - for RGB, R determines custom color, B used for offset, offset randomly applied R,G,B, in any combination

 - 3d picking system, hover over an entity on cam, if touching, it selects, circular highlight on touching, highlight size changes by entity size, if clicked on, highlight is yellow, open a GUI element with info 

 - selective breeding, the agents breed with nearby agents, hmm but all have the same RL policy?
 - species have certain survival requirements, say specific resources they must eat

 - chunk renders for performance (GPU split between RL and 3d env.)
 - anything not in cam not rendered?
 - the farther you are, smaller objects are not rendered

 - all models have a life cycle
 - hmm, if a model significantly branches off, do I add a new RL policy for it?

 - real sky-box, gradient sky effect, changes (dawn,dusk,noon, etc), clouds, change the sky-box for local weather, biomes

 - sun and moon in skys, lens flare effect when camera looks at the sun/moon, twinkling stars/ constellations (add a small reward for looking a constellations as an easter egg?) 

 - disease negative reward, add diseases?

 - wind effect for models, moves vertices depending on a flexibility factor

 - reward sleeping at night, energy bar per animal, neg reward for low energy, pos reward for high energy
 - max lifespan values, genetically change, reward for pass certain values of a lifetime