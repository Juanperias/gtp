# Math in GTL
as it is said in this specification one of the three types of GTL is number then we should have a system of arithmetic operations, these operations are the typical operations of addition subtraction multiplication among others, 

## How GTL processes mathematics
GTL itself does not have arithmetic operations as the values of the variables in GTL are always static before sending the request the arithmetic operations must be resolved, this in order to reduce server load, if an unresolved operation is sent to a GTP server it will respond with an error message.

## Using math in GTL
To use mathematics in GTL, it would be like any other programming language, e.g.
```
def n:test = 2 + 2 - 4 / 3 % (4 * 5)
```
furthermore, operations are solved from left to right and first solve what is inside the parenthesis.
