# interpreters be interpreting
this is going to be sooooo much fun. 

i dont even think i need to talk about which source im going to follow. it should be obvious. it starts with crafting and ends with interpreters. yes its crafting interpreters. the book be booking. 

### 21 nov, 2024:
ok so this guy portrays the process of a program being executed to climbing and descending a mountain. its actually a good analogy, so basically you take the user's code and pick out the tokens this is called lexing/scanning/lexical analysis(if you're a dickhead). next we take that and create a syntax tree (abstract syntax tree, parse tree, yada yada), this is where we establish the relationship between the tokens, for instance the var somevar = (a + b)/2 will be broken down into its tokens for example var will be taken out as a keyword then var will be taken in the parse tree as a system.var or something like that (basically telling the system that its a keyword) and the whole structure will be built out in the form of like a flow chart, this is called parsing. most of the programming languages have these two processes implemented in the same way. now we do static analysis, which is were we assign scope (scope resolution, binding) then we also do a type check here (if this is a statically typed language). now we reached the summit, so far what we've done is on the "front end". 

if you're a naive fool you will be thinking there is a backend. clearly you dont what curs these langauge wizards are. these swines have assigned a new term called "middle end", which is the most idiotic term to ever be conceived, but the concept is simple, we do not want to express our code in a "language" that can only be understood by a certain cpu architecture, we want it to be universal, so we express it in terms of some intermediate representation (IR).

now we do optmization, the author wants to skip it. he calls optimization phase as a rathole, not a rabbit hole, but a rat hole. he says most of the optimization can be done during the runtime. ok mr.languagewizardguy. now what we want to do is to convert this into a code the computer can actually run. we dont want to convert this into some asm code do we?? no no. we want to convert into bytecode so we can compile it on a virtual machine making sure that it runs on different architectures easily. they used to call bytecode p-code which i think is way way way better.

now we can do two things to convert that byte code into machine native code:
1. write a compiler for each architecture (mini compiler, this easy because we can just resue the compiler pipeline we just established)
2. write a virtual machine that emulates a chip and run the byte code on that

tree walk interpreter:
so basically we traverse the syntax tree one branch and leaf at a time evaluatinig each node as we go, this is not commonly used as it is slow. we're going to be making that. 

ok compilers vs interpreters bring it on, compilers just convert the source code into some machine executable format (bytecode) interpreters run the code one line at a time (by traversing the syntax tree).