# Agent-Based Model to investigate the effects of cooperation and different characteristics of Marine Protected Areas on a simulated artisanal fishery

> ## WHAT IS IT ?
An Agent-Based Model (ABM) that captures the main characteristics of an idealised small-scale, artisanal fishery. The modelcan be used to disentangle the combined effects of fishing behaviour (expressed by a cooperative trait associated to fishing effort), and different designs of no-take fishery areas (presence or absence, age, size, distance between two MPAs) on fish abundances and catches.

There are two types of agents, the fishing agents (pirogues with fishing crews) and fish agents. Agents are are initially randomly distributed on a finite two-dimensional space (fishing agents represented by circles, fish agents represented by triangles). Fishing agents are distinguished by different tonalities of grey, reflecting the associated cooperative trait values, ranging from fully-cooperative (black) to fully non-cooperative (lightest gray). 

The reproduction of fish agents is simulated as a stochastic process depending on a reproduction probability and on a logistic-type growth restriction. The movement of fish agents is simulated using three sensory zones around the fish, namely, repulsion zone, parallel-orientation zone, and attraction zone. The harvest rate of a fishing agent is described according to the classic Schaefer’s model.

> ## GENERAL ASPECTS

The file `CoopFishABM.py` contains the model code (in python) and is the script to run. The run generates (1) an subfolder named `/simulation_output`, which contains a video of the simulation (`simulation_video.mp4`), showing agents moving on the two-dimensional fishing ground and, if present, the MPA(s), (2) the data on the dynamics of fish abundance and catch (`simulation_data.csv`), and (3) snapshots of each computing time step of the simulation. 

> ##  RELEVANT MODEL PARAMETERS

* Set parameters for the configuration of the MPA (presence/absence, size, age, and distance of between two MPAs)

```
MPA = 'yes'         # Presence or absence of MPA ('yes' for presence, 'no' for absence)
Both = 'no'         # Presence of MPA ('no' for presence over full duration of simulation, 'yes' for presence over a period)
Time_MPA = 50       # Period of time over which MPA is active (when Both = 'yes') 
Type_MPA = 'single' # Spacial configuration of MPA ('spaced' for two MPAs, 'single' for one MPA)
Dist_MPA = 0.2      # Distance between two MPAs (when Type_MPA = 'spaced')
Frac_MPA = 0.25     # Fraction of fishing grounde covered by MPA(s)
```

* Set parameters for the configuration of different cooperative scenarios. Each fishing agent is characterised by one of five possible attributes (ranging from fully non-cooperative to fully cooperative) 

```
fully_noncoop = 4     # number of fully non-cooperative pirogues
noncoop = 4           # number of non-cooperative pirogues
cond_coop = 4         # number of conditional cooperative pirogues
coop = 4              # number of cooperative pirogues
fully_coop = 4        # number of fully cooperative pirogues
```

> ##  THINGS TO NOTICE

* How does a simulation with-MPA of a given configuration (size, age, or/ and distance between two MPAs) compares with same simulation without-MPA  in terms of fish abundance and catch?
* Does the speed of fish agent have any impacts on the conservation effects of an MPA of a specific configuration (size, age, or/ and distance between two MPAs) ?
* Does the different cooperation levels (regulation of catchability) affects the conservation effects of an MPA of a specific configuration (size, age, or/ and distance between two MPAs) ?

> ##  EXTENDING THE MODEL 

* In this model, we do not include life-history traits of the fish agents. Try extending the model by implementation of multiple fish species with different behavioural attributes and life-history traits.
* Complexity can be also added to fishing agents to investigate in more detail cooperative self-governance, which can be achieved with a variety of mechanisms, including monitoring, sanctioning, and reciprocity. 


















