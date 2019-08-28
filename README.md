# library-network-simulation
![Greetings!](materials/image_bipartite.png?raw=true "")

## Description
This repository is devoted to the simulation of a library networks.
The two types of nodes represent Books and Readers.
![Simulation example](materials/simulation.gif?raw=true "Simulation example")


## Parameters
### Graph initialization
```
params = {
  'n_books' : 50, # Number of Nodes in the Graph
  'n_agents' : 250, # Number of Agents (Actions per epoch, each agent trails its own path)
  'n_agents_init': 10, # Number of Agents at the simulation begining
  'seed' : None, # Integer seed number or None
  'epochs': 100, # Number of epochs
}
```

### Simulation events
Probabilities for an event happening at each event
One of those will be triggered by a single agent per epoch

#### Event1
There is a single event1 each epoch for every active agent
```
event1 = {
    '_alpha_': 20,   # P for adding a new node connected to an existing node chosen randomly according to the in-degree distribution
    'beta': 20,      # P for adding an edge between two exisiting nodes. One existing node is chosen randomly - according to the in-degree distribution and the other chosen randomly according to the out-degree distribution.
    'gamma': 20,     # P for adding a new node connected to an exsisting node chosen randomly  according to the out-degree distribution
    'delta_in': 20,  # Bias for choosing nodes from degree distribution.
    'delta_out':20   # Bias for choosing nodes from out-degree distribution.
} 
```
#### Event2
This event hapens right after event1. Each type of it happens once per epoch except 'eta'
```
event2 = {
    'epsilon': 0, # P for no event
    'zeta': 15,   # P for a new agent at a random node
    'eta': 25,    # P for an agent inviting a new agent (should also be influenced by a node's feedback)
    'theta': 10,  # P for adding a new book
    'iota': 0,    # P for activating a non-active user
    'kappa': 30   # P for deactivating an active user - there is a higher probability of retirement if more active
}
```
