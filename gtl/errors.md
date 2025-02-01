# Lang errors
This part of this document describes the possible errors when parsing GTL code, clients should display these errors exactly as described.
## Unrecognized expression < E >
This error occurs when using a reserved word that does not exist, e.g.
```
return 03
# Lang errors
This part of this document describes the possible errors when parsing GTL code, clients should display these errors exactly as described.

As a recommendation (although this specification does not require the following) is that at the beginning of any error the line in which the error occurred should be shown 

## Unrecognized expression < E >
This error occurs when using a reserved word that does not exist, e.g.
```
return 03
# Unrecognized expression return 0
```
## Invalid expression < E >
This error occurs when the GTL code is misspelled even if the reserved words are correct, e.g.
```
"Hello!" msg s:def
# Invalid expression "Hello!" msg s:def
```
## Incorrect type < T > expected < T >
This error occurs when a data type is assigned a value that is of another data type, for example, a variable that is a number is assigned a string or defined as a graph.
```
def n:age = "GTL is good"
#  Incorrect type String expected Number
```
## Undefined variable < V >
This error occurs when using a variable that has not been defined.
```
def n:sum = 2 + random_number
# Undefined Variable random_number
```
### 
This error will also happen when you try to make a relationship between two graphs and one of the graphs does not exist.
## Cannot divide by zero
This error occurs when trying to divide by zero.
```
def n:special_number 0 / 0
# Cannot divide by zero
```
### Expression < E > cannot be used in mode < M >
This occurs when we use a reserved word in a mode for which it is not intended.
```
set kind 1
# ...
ret 0
#  Expression ret cannot be used in mode 1
```




