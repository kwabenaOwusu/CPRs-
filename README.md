# common_pool_uncertainty model

## Usage
The model code is implemented in python. To run the model, you need to place **pycxsimulator.py** in the same directory where **common_pool_uncertainty.py** is located.

**Overview** {#overview .unnumbered}
------------

### Purpose {#purpose .unnumbered}

We develop an agent-based model to study the impact of different uncertainty levels regarding the resource size as well as social interaction, i.e. number of other agents located within a neighbourhood radius, on the harvesting behaviour of a group of fishermen exploiting a common pool resource. The model is developed for decision makers on management of renewable natural resource to help advance the design of resource management interventions.

### Entities, state-variables and scales {#entities-state-variables-and-scales .unnumbered}

The model has two agents, namely a fisherman and fish agent which lives in a two dimensional world. Every agent has a position (x and y coordinates) and changes this position by a random amount in discrete time. The movement on the two-dimensional world occurs within torus landscape (i.e. when agents approach a border of the landscape, they re-enter the system at the opposite border). A fishermen can only harvest fish in a neighbourhood radius ($r$) centred at it.

### Process overview and scheduling {#process-overview-and-scheduling .unnumbered}

Fishermen form a perception of the number of fishes. There is a random difference between the true and perceived number of fishes. We explicitly modeled this difference as a Gaussian probability distribution a mean of the true number of fishes ($N_{f}$) and a standard deviation ($U_{f}$), which represents the extent to which perception of the number of fishes of all the fishermen as a whole can deviate from the true number of fishes. The harvesting behaviour of a fisherman is determined by its harvesting coefficient, which is quantified as the absolute difference between its perceptions of the number of fishes from the true number of fishes. The harvesting coefficient also decreases by a constant factor for each other fisherman located in a fisherman’s neighbourhood radius. Hence, a higher number of other fishermen in neighborhood radius result in a lower harvesting coefficient. For harvesting to occur the following condition must be satisfied

<span>0.9</span>

$$mbox{ random-uniform (0,1)}  <  (alpha - beta ast n_{f}) label{eq3}$$

where $alpha $ is the harvesting coefficient of the fisherman scaled between 0 and 1, $ n_{f}$ is the number of other fishermen in neighbourhood radius, $beta$ is a factor of reduction in harvesting coefficient for each fisherman within the neighbourhood radius, and $mbox{ random-uniform (0,1)} $ is a uniform distribution of evenly distributed values over a specified range (minimum value of 0 and a maximum of 1).

In other words, a random number is drawn from the uniform distribution and if it is less-than the right-hand-side (R.H.S) expression of [eq3], a fish in neighbourhood radius is harvested. This condition ([eq3]) is executed once for each fish agent in the neighbourhood radius. Thus, with a high harvesting coefficient and low number of other fishermen, a fisherman is more probable to harvest a larger fraction of the fishes in its neighborhood radius. The fishermen moves by setting the heading towards the direction of any fish they sight (there is an equal probability of sighting or not sighting a fish) and moving a fixed-magnitude ($M_{F}$) forward. If no fish is sighted, then the fisherman set a random-heading and moves fixed-magnitude forward.

The fish agent growth rate is according to a logistic growth rate restriction. A copy of a randomly selected fish agent is created as an offspring if

<span>0.9</span>

$$mbox{ random-uniform (0,1)}  <  R left(1- frac{N_{f}}{K}right) label{eq4}$$

where $R$ is the growth rate probability of the fishes, $N_{f}$ is the number fishes and $K$ is the carrying capacity. Thus growth stops when $N_{f}$ equals $K$ and high values of $R$ increases the growth rate of the fishes.

The fish moves in a random-walk by setting heading to a random angle and moving a fixed-magnitude ($M_{f}$) forward. The newly reproduced fish starts its life at the location of its parent but however diffuses with time as they make random movements.

### **Design Concepts** {#design-concepts .unnumbered}

### Theoretical and Empirical Background {#theoretical-and-empirical-background .unnumbered}

Theoretical and background hypothesis underlying the model design of environmental uncertainty on harvesting behaviour is inspired by the works of [@budescu1990resource; @andras2006uncertainty; @gustafsson1999overharvesting; @rapoport1992social; @schill2016cooperation; @kortenkamp2006time]. The influence of a fisherman’s interaction with other fishermen on harvesting behaviour is also motivated by the works of [@huff2015agent; @agrawal2013interactions; @little2007simulations]. The logistic growth rate of the fishes is based on the work of [@clark2010mathematical; @schaefer1991some].

### Individual Decision-Making {#individual-decision-making .unnumbered}

Fishermen make individual decisions on harvesting coefficient to exert which is determined by perception of the number of fishes and the number of other-fishermen in its neighbourhood radius. The spatial location of a fisherman influences its decisions as it determines the number of other fishermen in neighbourhood radius.

### Interaction, Sensing and Observation {#interaction-sensing-and-observation .unnumbered}

Interaction occurs between the fishermen when they share a common fishes in their neighbourhood radius. If the fishes are first harvested by one of the fishermen, it remains unavailable of the other fishermen. Interaction between fisherman and fish agent occurs when the fishermen sight a fish and moves in its direction. A fisherman’s fishing capacity is limited to only fishes in its neighbourhood radius hence, the spatial scale of sensing is local. A time-plot of the number of fishes and harvest of the fishermen is displayed.

### **Details** {#details .unnumbered}

Each step in the model represents a year and we run the simulations for 250 years or until all the fishes get depleted, whatever occurs first. The model code is implemented in python and the source code is openly available at (<span>[https://github.com/kwabenaOwusu/CPRs-](https://github.com/kwabenaOwusu/CPRs)</span>).

### Initialization {#initialization .unnumbered}

### Input {#input .unnumbered}

The model does not make use any external data files.

### Submodels {#submodels .unnumbered}

All the sub-models employed are as already described in the process overview and scheduling.

