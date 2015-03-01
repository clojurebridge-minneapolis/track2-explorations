# Twenty Questions

This morning, for the game of 20 questions we represented the network of questions as a static data structure and had a function traverse it to implement our program.

But instead of representing the nodes of the network as a map, we can represent them as closures. Can you re-write the function `make-node` to return a function instead of a map?

Hint: The function returned will need to take the network in parameter to fetch the next node.

What are the advantages/inconvenients of representing a network with closures compared to the more traditional approach of data structure + function? What if we want to change the topology of the network at runtime? What if we want to change the semantics of a node at runtime?

As it is, the program still has to lookup each node in the network at runtime. We could further improve our program by calling the next node directly instead of having to look the node up at runtime. Can you write a function `compile-net` that takes a static description of the network as a map (See `make-node` from this morning), and the name of a node in the network and return a function that implements the program starting from this node.

Hint: `compile-net` will call itself.
