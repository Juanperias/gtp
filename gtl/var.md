# Variables
something very basic of GTL are the variables that allow us to store information (not always in a persistent way) now if you saw main md you will know how to define a variable, in this part we talk about how variables are handled.

## Non-persistent variables
The non-persistent variables are variables that as its own name says it do not have any type of persistence but of the context of the request, this is done to save some space at the moment of saving variables, the types of variables that are not persistent are these types:
- Numbers
- strings
- nodes
- relations

Wait?! why are the nodes and relations in that list, the answer is simple if a node is defined even if it has several relations must be in a graph (which is the only persistent type) if that node is defined in a graph then it will be persistent.

## Persistent variables
Persistent variables are extremely important as their name says they are variables that are saved by the server and can be obtained with a query (read the query specification in gtl/query) in this case this type of variables must be graphs as they are graphs the nodes and relationships that make up the graph will be saved.

## How to save persistent variables
As this protocol is designed to be simple to understand then saving persistent variables should also be simple, now in this case GTP is quite flexible on how persistent variables should be saved, but they must meet a number of requirements:
- No modifications to GTL syntax required
- no changes should occur when returning information from the server.
