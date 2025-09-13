# Ex-2-GENERATION OF LEXICAL TOKENS LEX FLEX TOOL
# AIM
## To write a lex program to implement lexical analyzer to recognize a few patterns.
# DATE : 01.09.2025
# ALGORITHM

1.	Start the program.

2.	Lex program consists of three parts.

     a.	Declaration %%

     b.	Translation rules %%

     c.	Auxilary procedure.

3.	The declaration section includes declaration of variables, maintest, constants and regular definitions.
4.	Translation rule of lex program are statements of the form

    a.	P1 {action}

    b.	P2 {action}

    c.	…

    d.	…

    e.	Pn {action}

5.	Write a program in the vi editor and save it with .l extension.

6.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l $ cc lex.yy.c
7.	Compile that file with C compiler and verify the output.

# INPUT
```

%{
 int COMMENT=0;
%}
identifier [a-zA-Z][a-zA-Z0-9]*
%%
#.* { printf("\n%s is a PREPROCESSOR DIRECTIVE",yytext);} 
int | float | char | double | while | for | do | if |
break | continue | void | switch | case | long | struct | const | typedef | return | else |
goto {printf("\n\t%s is a KEYWORD",yytext);}
"/*" {COMMENT = 1;}
"*/" {COMMENT = 0;}
{identifier}\( {if(!COMMENT)printf("\n\nFUNCTION\n\t%s",yytext);}
\{ {if(!COMMENT) printf("\n BLOCK BEGINS");}
\} {if(!COMMENT) printf("\n BLOCK ENDS");}
{identifier}(\[[0-9]*\])? {if(!COMMENT) printf("\n %s IDENTIFIER",yytext);}
\".*\" {if(!COMMENT) printf("\n\t%s is a STRING",yytext);}
[0-9]+ {if(!COMMENT) printf("\n\t%s is a NUMBER",yytext);}
\)(\;)? {if(!COMMENT) printf("\n\t");ECHO;printf("\n");}
\( ECHO;
= {if(!COMMENT)printf("\n\t%s is an ASSIGNMENT OPERATOR",yytext);}
\<= |
\>= |
\< |
== |
\> {if(!COMMENT) printf("\n\t%s is a RELATIONAL OPERATOR",yytext);}
%%
int main(int argc,char **argv)
{
if (argc > 1)
{
FILE *file;
file = fopen(argv[1],"r"); if(!file)
{
printf("could not open %s \n",argv[1]); exit(0);
}
yyin = file;
}
yylex(); printf("\n\n"); return 0;
} int yywrap()
{
return 0;
}

```
# OUTPUT
<img width="958" height="1001" alt="image" src="https://github.com/user-attachments/assets/0806837e-65d3-4ae2-a596-6062ffe99f67" />
<img width="949" height="463" alt="image" src="https://github.com/user-attachments/assets/b9a20f79-ead0-45bb-ad14-dfcbe28a5225" />


# RESULT
## The lexical analyzer is implemented using lex and the output is verified.
