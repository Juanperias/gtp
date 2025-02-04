# Queries
Everything is going well with GTL so far; we can send information to the server. However, we cannot retrieve information from the server or the information we previously stored. This issue is resolved with queries, which allow us to obtain information from the server (important: the server can set query limits with a query-rule).

queries make an exception we can use server context even if the kind is request! however queries can not be used if the kind is response

## Making queries in GTL
Queries in GTL are quite simple, they are formed from the reserved word query and what you need to ask the server, the server must respond with a response to that query (as long as it follows the query-rules).
```
query $g # Requesting all graphs
```
Now the queries are made only to obtain information if the client wants to do something with that information it should not be done directly in GTL.

### Where do we get the queries clauses from
In the previous example we used $g which is a Server-context, it is important to remember that in the queries we can use server contexts to reference the information we want.

# Query rules
all very well now, but what if we want to make some rules in the queries to limit the server contexts that can be used, the query rules are really simple, it is simply a native way of the protocol to delimit the references of the server contexts that can be used, this is not done directly in GTL but inside GTP.
