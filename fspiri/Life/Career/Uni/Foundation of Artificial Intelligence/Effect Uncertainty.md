# Effect Uncertainty
In some case the agent knows the effects of its actions. That is, given a state it can predict the state resulting from carrying out that action in state state. Most of the times however the agents have a certaing probability of an effect occurring.

The **effect uncertainty dimensions** is the the dynamics can be:
- **deterministic** - when the state resulting from an action is determined by an action and the prior state
- **stochastic** - when there is only a probability distribution over the possible results

This dimensions onnly makes sense is the environment is fully observable, because the stochastic dimensions can be linked to a unobservable part of the environment.


### Why Probability?
An agent must act even if its not **certain**
- **definite predictions** - you will die tomorrow
- **distribution** - be careful and you won't die tomorrow
- **point probability** - 0.2 Death, 0.05 if you're careful
- **probability** - die with probability in range [0.01 - 0.3]