# FormatValidation

You will write a python script that is capable of validating the format of an assignment statement in a pretend language as specified below. Potential statements to verify will be contained in a file, one per line, where the name of the file is specified as a command line argument. The parsing process will be done incrementally using regular expressions and the intermediate results will be printed out along the way. The format of a statement is described below.

Statements can be composed of various operators and operands according to a special format which has very little to do with actual Python syntax. The first phase of parsing is to find potential operands. An operand can be either a variable name or a literal integer or real number. A variable name has two forms: 1) an integer variable has a name which begins with a lower case i followed by one or more letters, 2) a real variable has a name which begins with a lower case r followed by one or more letters. A literal integer can have an optional plus or minus sign to start, followed by a series of digits beginning with a non-zero digit, unless the value is 0 itself. A literal real number begins as an integer does, but is then followed by a period, and at least one digit. You should replace occurrences of integer variable names with the word varint. You should replace occurrences of real variable names with the word varreal. You should replace occurrences of real literals with the word litreal. You should replace occurrences of integer literals with the word litint. You should print out intermediate versions of the expression string after replacements for each type of operand have occurred.

There are six valid operators: 1) = is the assignment operator, 2) + is for integer or real addition, 3) - is for integer or real subtraction, 4) * is for integer or real multiplication, 5) / is for real division, and 6) // is for integer division. You should replace occurrences of these operators with the corresponding words: opequal, opadd, opsub, opmult, oprdiv and opidiv. You should print out intermediate versions of the expression string after replacements for each type of operator have occurred. After having done all of the operand and operator replacements, if there is anything in the revised expression other than the four words for operands and the six words for operators, an error message should be printed and the processing stopped for this expression.

The second layer of parsing is to recognize various terms in the expression that involve multiplication and division operators. The definition of an integer term is the following: a varint or litint followed by opmult or opidiv followed by another varint of litint. It is represented by the word termint. It is also possible for an integer term to begin with the word termint rather than varint or litint. The definition of a real term is the following: a varreal or litreal followed by opmult or oprdiv followed by another varreal or litreal. It is represented by the word termreal. It is also possible for a real term to begin with the word termreal rather than varreal or litreal. You should replace all occurrences of the terms involving multiplication and division by the appropriate words termint and termreal and print out the revised expression. If there are any occurrences of opmult, oprdiv or opidiv after this step, an error message should be printed and the processing stopped for this expression.

The third layer of parsing is to recognize various subexpressions in the expression that involve addition and subtraction operators. The definition of an integer subexpression is the following: a varint, litint or termint followed by opadd or opsub followed by another varint, litint or termint. It is represented by the word subint. It is also possible for an integer subexpression to begin with the word subint rather than varint, litint or termint. The definition of a real subexpression is the following: a varreal, litreal or termreal followed by opadd or opsub followed by another varreal, litreal or termreal. It is represented by the word subreal. It is also possible for a real subexpression to begin with the word subreal rather than varreal, litreal or termreal. You should replace all occurrences of the subexpressions involving addition and subraction by the appropriate words subint and subreal and print out the revised expression. If there are any occurrences of opadd or opsub after this step, an error message should be printed and the processing stopped for this expression.

The final expression check is to see if a valid statement remains. It takes one of two forms: 1) a varint followed by opequal followed by a litint, varint, termint or subint, or 2) a varreal followed by opequal followed by a litreal, varreal, termreal or subreal. If you find such a pattern it should be replaced by the word statement and the resulting string should be printed out. If there is anything left in the expression string other than the word statement, an error message should be printed out. You should process all lines of the file in this manner. 

Submit your commented source code here, along with a sample input file of text expressions and the corresponding output generated by the program for these test expressions.