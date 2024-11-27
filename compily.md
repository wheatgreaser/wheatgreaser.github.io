# interpreters be interpreting
this is going to be sooooo much fun. 

i dont even think i need to talk about which source im going to follow. it should be obvious. it starts with crafting and ends with interpreters. yes its crafting interpreters. the book be booking. 

## 21 nov, 2024:
ok so this guy portrays the process of a program being executed to climbing and descending a mountain. its actually a good analogy, so basically you take the user's code and pick out the tokens this is called lexing/scanning/lexical analysis(if you're a dickhead). next we take that and create a syntax tree (abstract syntax tree, parse tree, yada yada), this is where we establish the relationship between the tokens, for instance the var somevar = (a + b)/2 will be broken down into its tokens for example var will be taken out as a keyword then var will be taken in the parse tree as a system.var or something like that (basically telling the system that its a keyword) and the whole structure will be built out in the form of like a flow chart, this is called parsing. most of the programming languages have these two processes implemented in the same way. now we do static analysis, which is were we assign scope (scope resolution, binding) then we also do a type check here (if this is a statically typed language). now we reached the summit, so far what we've done is on the "front end". 

if you're a naive fool you will be thinking there is a backend. clearly you dont what curs these langauge wizards are. these swines have assigned a new term called "middle end", which is the most idiotic term to ever be conceived, but the concept is simple, we do not want to express our code in a "language" that can only be understood by a certain cpu architecture, we want it to be universal, so we express it in terms of some intermediate representation (IR).

now we do optmization, the author wants to skip it. he calls optimization phase as a rathole, not a rabbit hole, but a rat hole. he says most of the optimization can be done during the runtime. ok mr.languagewizardguy. now what we want to do is to convert this into a code the computer can actually run. we dont want to convert this into some asm code do we?? no no. we want to convert into bytecode so we can compile it on a virtual machine making sure that it runs on different architectures easily. they used to call bytecode p-code which i think is way way way better.

now we can do two things to convert that byte code into machine native code:
1. write a compiler for each architecture (mini compiler, this easy because we can just resue the compiler pipeline we just established)
2. write a virtual machine that emulates a chip and run the byte code on that

tree walk interpreter:
so basically we traverse the syntax tree one branch and leaf at a time evaluatinig each node as we go, this is not commonly used as it is slow. we're going to be making that. 

ok compilers vs interpreters bring it on, compilers just convert the source code into some machine executable format (bytecode) interpreters run the code one line at a time (by traversing the syntax tree).

## 24 nov, 2024:
sometimes i hate myself. this is one of those times, ive just begun to realize the magnitude of the project ive taken up. the process of scanning/lexing where we comb through the code line by line to pick out the individual keywords is itself a whole 60 page chapter in this book. on a scale of 1 - 10 im about 7 in terms of "cooked". so there is that, i downloaded the repo, blew off the dust (there wasnt any its digital dumbass its a joke) and then i ran it. the language itself is a "scripting language" which means it directly runs from the source. 

we could categorize tokens just by comparing raw strings (which is the form of implementation i would have thought up) but instead its better to created an enum that has the different type of strings so that we can also classify it into the type of lexeme to which it belongs. 

ok what the fuck is a lexeme, i hear you think. well, let's say there's an expression like:

```
var shit = "fuck";
```

now var, shit, =, "fuck", ; are all lexemes. when we do error handling its good to show the location fo the error too ("missing ; in line 4"). in case youre like me and you're wondering what the fuck is the idfference between a token and a lexeme, well, a lexeme is the concrete use of a token. the job of the lexer/scanner is to classify the lexeme into tokens (if it encounters the lexeme "if" it will recognie if as a keyword token of the enum(type) if). 

ok so here's my plan what im going to do is follow the books, then make my own implementation of each chapter in c++, because ill learn c++ while at the same time learning the concepts more clearly, apparently this is a very popular approach in learning this book. 

## 26 nov, 2024:
ok in c++ terms what we want is to take an input (a string input) and return a vector of tokens. this is super exciting because here is where we do all the keyword shit, so instead of let or var or something (incase we wont to be sinners and make our language dynamically typed) we can have "set" or something silly. 

ok so we can create struct which has the TokenType value (an enum is basicaly like a programmer-defined type for thsoe of you new to c++, so instead of specifying the "type" by using a string or something we can create a type on our own) and a string that contains the user defined value for example if the user writes
```
set isGooningTime = true
```
then set will be of the TokenType Set, isGooningTime of the type variable and will have the string as "isGooningTime" and "=" will have the type Equals and then "true" will have the TokenType as boolean and the string will be "true".

the rest of the program is just boring old splitting the string into several and seperate words and classify them into seperate types typa thing. 
