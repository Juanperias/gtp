# Getting started with GTL
Gtl is designed to be simple to understand, most of the GTL stuff is oriented to define graphs and interact with the responses, when you make a request to a GTP server it must execute the GTL code of the request, the GTL code is like the dna of the request defines what to do or what I want to get, the server in turn also responds with a GTL header but simplified.

## Lang items

### Data types in GTL
GTL is made up of only 3 data types
- string:  a character string with dynamic length something like the String data type of rust
- number: perhaps the simplest type, number is a 32-bit integer.
- graph: The most complex data type is a combination of the three types, it requires the use of strings and numbers, make sure you have correctly implemented all these data types before the graph.
these data types are the ones that form the whole GTL and must be implemented by the GTP client and server.

### Creating variables
Variables in GTL cannot be dynamic, they must have a known value and null variables cannot be declared. Variables within GTL are defined with the reserved word **def**
```
def type(number/n, string/s, graph/g):name val
def n:age 18
def s:name "juan"
def g:graph (100, 100) 20 "hello!" # (pos) weight name
```
### Graphs
The data type of the graphs is the most powerful and the one that needs more explanation, from this data type turns the whole language, when you define a graph the server could save the graph like this
```rust
struct Graph<'a> {
	weight: u32,
	pos: (u32, u32),	
	name: String,
	relations: Vec<&'a Graph<'a>>
}
```
Relationships are connections to other networks that also have more relationships to other networks.

To connect graphs with GTL it can be something like this
```
def g:graph (100, 100) 20 "hello!"
def g:graph2 (150, 100) 2 "hello 2!"
graph>graph2
```


## GTL kind header
GTL has two types for requests and for server responses, these types are taken in different ways depending on the kind variable, this has two possible states 1 (req) 0 (res), when kind is 1 you can send requests to save networks, or to ask the server for the networks that are found, while a request with type 0 is more structured to be simple to process. 

To set this header we can use set
```
# response
set kind 0
set origin 0.0.0.0:3000 
# request
set kind 1
```
Origin is extremely important, if kind is 0 and origin is not in the header, the client should automatically reject the response from the server.


## Server-side
We have seen much of GTL on the client side, but now we will see how gtl works on the server side.

First of all there are big changes like for example the GTL header is forced to return something to return something the reserved word **ret** is used something like this
```
ret 0 # return 0
```
In this case what we return will be the response the customer will receive.

It is important to clarify that if the header is kind = 1 the reserved word **ret** cannot be used, because it will be GTL code destined to make requests and requests can NOT return something.

## Server context
The server context is a set of defined variables that are found on the server and hydrated into the GTL code. These variables cannot be passed directly to the client and there must be a process where this is converted to the expected content.

The following is a table of the server context
| Name | Value |
|------|-------|
| $g   |  all networks that have been stored  |
| $gl   | number of stored graphs   |


