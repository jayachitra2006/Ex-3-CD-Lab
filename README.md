# Ex-3-RECOGNITION-OF-A-VALID-ARITHMETIC-EXPRESSION-THAT-USES-OPERATOR-AND-USING-YACC
# Date:08/05/2025
# AIM
To write a yacc program to recognize a valid arithmetic expression that uses operator +,- ,* and /.
# ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the operators =,+,-,*,/ and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter an arithmetic expression as input and the tokens are identified as output.
# PROGRAM!
```
cd3.l
%{
#include "y.tab.h"
%}

%%

"=" {printf("\n Operator is EQUAL");} 
"+" {printf("\n Operator is PLUS");}
"-" {printf("\n Operator is MINUS");} 
"/" {printf("\n Operator is DIVISION");}
"*" {printf("\n Operator is MULTIPLICATION");} 
[a-zA-Z]*[0-9]* {
printf("\n Identifier is %s",yytext); return ID; }
. return yytext[0];
\n return 0;

%%

int yywrap()
{
return 1;
}
cd3.y
%{
#include <stdio.h>
#include <stdlib.h>
%}

%token ID

%%

statement:
      ID '=' E        { printf("\nAssignment expression is valid\n"); }
    | E               { printf("\nValid arithmetic expression\n"); }
    ;

E:
      E '+' ID        { }
    | E '-' ID        { }
    | E '*' ID        { }
    | E '/' ID        { }
    | ID              { }
    ;

%%

int main() {
    printf("Enter an expression:\n");
    return yyparse();
}

void yyerror(char *s) {
    fprintf(stderr, "Error: %s\n", s);
}
```


# OUTPUT
![Screenshot 2025-05-08 144024](https://github.com/user-attachments/assets/d0768489-633f-4376-84a1-b6e3b3d3d394)


# RESULT
A YACC program to recognize a valid arithmetic expression that uses operator +,-,* and / is executed successfully and the output is verified.
