# Rantanplan
Joan Espansa's version of Rantanplan, updated to allow compilation on Mac OSX.

Here is how this version was made:

The original version Rantanplan is a pure SAT planner.  Clone from [https://github.com/marvinwilliams/rantanplan](https://github.com/marvinwilliams/rantanplan).

The SMT version of Rantanplan by Joan Espansa can be cloned from [https://github.com/JoanEspasa/rantanplan-public](https://github.com/JoanEspasa/rantanplan-public).  To install it, follow the steps below.

Install antlr3c:

    homebrew install libantrl

Edit Makefile in rantanplan/src/ to set

        CFLAGS += -I/usr/local/include
        LFLAGS += -L/usr/local/lib

Edit src/encodingUFVisitorZ3.cpp to change the line:

        Z3_ast ast = Z3_parse_smtlib2_string(*con, constraint.c_str(),

to:

        Z3_ast ast = (Z3_ast) Z3_parse_smtlib2_string(*con, constraint.c_str(),
        
Finally,

    cd rantanplan-public/src
    make
    cp parser ~/bin/rantanplan

