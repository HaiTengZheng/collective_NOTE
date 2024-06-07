# variables
- It is standard practice for every makefile to have a variable named `objects`,
    `OBJECTS`, `objs`, `OBJS`, `obj` or `OBJ` which is a list of all object of 
    all object file name.

# Deduce the Recipes
It has an implicit rule for updating a '.o' file from a correspondingly named
`.c` file using a `cc -c` command.
