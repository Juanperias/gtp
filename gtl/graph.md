# Graphs

The graphs are practically the most important part of this protocol, therefore GTL requires to have an excellent graph handling system, in this part it is explained how to handle the handling of the node data type and the relation data type.

#  Node Data type
graphs like other data types remain the same (unlike arithmetic which is solved before sending the package), for a graph implementation you must have these types already implemented
 - numbers
 - strings
it should also be possible to use tuples (to represent the position of the graph).
## How to create a node in GTL
The syntax of a node in GTL is meant to be simple, a network is defined as follows
```
# (pos) weight content
def n:name = (20, 20) 10 "content of the graph!"
```
# Relations
As we know in graph theory, nodes are related to each other, so it is important to establish some type of relationship. Although relationships can be stored in a variable, each relationship must start with a node, and the nodes they connect to are stored in the node's information. The relationships of a node can be obtained through a query.
```
def n:jhon  $ 1 "developer"
def n:maria  $ 1 "developer"
def n:pepe $ 2 "employer"

2:pepe>maria,jhon
```

First, you put the weight of the relationship, then the node, and then the nodes they are related to (if there are more than one, they are separated by a comma).

This doesn't necessarily mean that Maria and John are connected to each other, but if both are connected to Pepe, we can also just connect Maria and Pepe. We can do this.
```
1:pepe>maria
```
# Graph
The graph is the most important data type, but it is made up of nodes (there's no need to specify the relationships because the nodes already have the relationships).
```
def g:my_graph pepe,maria # We exclude jhon
def g:jhon_graph maria.jhon
```
The graph is persistent (like the nodes). Numbers and strings, unless they are part of a node, do not go beyond the package that defines them. This is important to understand, and in addition, graphs are indexed by the hash (this is better explained in gtl/query.md).

