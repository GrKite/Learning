## Using Cursor Variables (REF CURSORs)

Like a cursor, a cursor variable points to the current row in the result set of a multi-row query. A cursor variable is more flexible because it is  not tied to a specific query. You can open a cursor variable for any  query that returns the right set of columns.

You pass a cursor variable as a parameter to local and stored  subprograms. Opening the cursor variable in one subprogram, and  processing it in a different subprogram, helps to centralize data  retrieval. This technique is also useful for multi-language  applications, where a PL/SQL subprogram might return a result set to a  subprogram written in a different language, such as Java or Visual  Basic.

Cursor variables are available to every PL/SQL client. For example,  you can declare a cursor variable in a PL/SQL host environment such as  an OCI or Pro*C program, then pass it as an input host variable (bind  variable) to PL/SQL. Application development tools such as Oracle Forms, which have a PL/SQL engine, can use cursor variables entirely on the  client side. Or, you can pass cursor variables back and forth between a  client and the database server through remote procedure calls.



### What Are Cursor Variables (REF CURSORs)?

Cursor variables are like pointers to result sets. You use them when you want  to perform a query in one subprogram, and process the results in a  different subprogram (possibly one written in a different language). A  cursor variable has datatype `REF` `CURSOR`, and you might see them referred to informally as `REF` `CURSOR`s.

Unlike an explicit cursor, which always refers to the same query work area, a  cursor variable can refer to different work areas. You cannot use a  cursor variable where a cursor is expected, or vice versa.



### Why Use Cursor Variables?

You use cursor  variables to pass query result sets between PL/SQL stored subprograms  and various clients. PL/SQL and its clients share a pointer to the query work area in which the result set is stored. For example, an OCI  client, Oracle Forms application, and Oracle database server can all  refer to the same work area.

A query work area remains accessible as long as any cursor variable  points to it, as you pass the value of a cursor variable from one scope  to another. For example, if you pass a host cursor variable to a PL/SQL  block embedded in a Pro*C program, the work area to which the cursor  variable points remains accessible after the block completes.

If you have a PL/SQL engine on the client side, calls from client to  server impose no restrictions. For example, you can declare a cursor  variable on the client side, open and fetch from it on the server side,  then continue to fetch from it back on the client side. You can also  reduce network traffic by having a PL/SQL block open or close several  host cursor variables in a single round trip.