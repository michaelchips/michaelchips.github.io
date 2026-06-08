---
title: How Compilers & Interpreters Work 01 := Lexical Analysis
date: 2026-06-08
draft: false
tags:
---
Hello! This post is the first of a series of short posts going through what I learn as I research how compilers work. This is to help me write my Volq programming language, although last year I could've taken a module at university about compilers but I chose other modules instead, so now I'm researching it on my own.

A Lexical Analyser, or a lexer or scanner for short, is the first component of a compiler that processes your source code. It is also relevant in areas such as Natural Language Processing (NLP), for example, your prompt being turned from text into tokens when you're talking to your favourite LLM, like ChatGPT or Claude etc.

A lexer reads source code of a program as its input. It scans the characters in the source code and then separates a group of characters into a **lexeme**, which is an individual segment of code with a certain meaning. For example, directives such as `if` or `while`, or variable names and what operators and values they're initialised with. 

The **lexeme** is then matched to a certain **type of token** depending on what it is. For example, in the case of the lexeme `while`, this is a word reserved to the programming language and is outputted as a `KEYWORD` token. Another lexeme `dog` could be outputted as a `IDENTIFIER` or a `LITERAL`, depending on whether it's a variable or function name, or data in the form as a string. 

This cycle is repeated until the end of the source code is reached, and the result is a stream of tokens representing all the source code provided. The lexer **does not** understand the meaning of the program and what it is doing. The only logical decisions it makes are separating out lexemes and categorising them into a type of token.

There are several types of tokens:
- **Keyword**
	- A reserved word in the programming language with a fixed meaning
	- A keyword cannot be used as a variable name
	- Examples include: `if`, `else`, `while`, `do`, `return`, `int`, `class`
- **Identifier**
	- A name chosen by programmer for something defined in source code, such as a variable, function or class
	- Examples include: `x`, `counter`, `harmonicSum`, `Stack`
- **Literal/constant**
	- A fixed value written in source code by the programmer
	- Examples include: `5`, `3.14`, `"thisisastring"`, `'W'`, `true`, `false`
- **Operator**
	- A symbol with a defined arithmetic or comparison operation to perform on compatible values
	- May take two operands (binary), e.g. `2 + 2`, or only one operand (unary), e.g. `3++`
	- Examples include: `+`, `-`, `*`, `/`, `=`, `==`, `>=`, `<=`, `&&`, `||`
- **Separator**
	- A symbol that groups or isolates other tokens in the source code
	- For some languages, separators can act as delimiters for ending lines of code, e.g. ; in Java
	- Examples include: `;`,  `:`, `(`, `)`, `{`, `}`, `[`, `]`
- **Comment**
	- Extra text added into the source code which is ignored by the compiler
	- Some lexers may pass comments to the parser, others may discard them first
	- Not ignored during literate programming, i.e. generating Javadoc
	- Examples include: `# This is a Python style comment`, `// This is a Java style comment`, `/* This is a Java style inline comment and multi-line comment block */`
- **Newline**
	- Line break in the source code, i.e. every time the programmer presses the enter key
- **Indent and Dedent**
	- Increasing or decreasing the level of indentation to help group blocks of code
- **EOF**
	- EOF is short for End Of File; it indicates the lexer has reached the end of the file and there are no more characters to process

Different lexers may treat some tokens differently, for example, some languages with the syntax convention to separate lines of code with line breaks, would pass all Newline tokens to the parser. Others that use a different syntax convention, semicolons to indicate the end of a code statement for example, may **ignore** generating Newline tokens.

Let's look at an example of lexing a small Python-esque program into tokens. It doesn't do much, it just asks the user for their favourite colour and responds with either me too or good choice.

```py
# Take input from user
answer = input("What's your favourite colour?")
if answer == "purple":
	print("Me too!")
else:
	print("Good choice.")

# End of program
```

And now lets look at the possible output of tokens after being analysed by a lexical analyser:

```
COMMENT( Take input from user)
NEWLINE

IDENTIFIER(answer)
OPERATOR(=)
IDENTIFIER(input)
SEPARATOR(()
LITERAL("What's your favourite colour?")
SEPARATOR())
NEWLINE

KEYWORD(if)
IDENTIFIER(answer)
OPERATOR(==)
LITERAL("purple")
SEPARATOR(:)
NEWLINE

INDENT
IDENTIFIER(print)
SEPARATOR(()
LITERAL("Me too!")
SEPARATOR())
NEWLINE

DEDENT
KEYWORD(else)
SEPARATOR(:)
NEWLINE

INDENT
IDENTIFIER(print)
SEPARATOR(()
LITERAL("Good choice.")
SEPARATOR())
NEWLINE

DEDENT
COMMENT( End of program)
EOF
```

This might seem a bit long or confusing, but really this is exactly the same short code snippet, just now in token form! I've added line breaks after each `NEWLINE` token to make it easier to read, but these wouldn't be present in real output.

Although `input` and `print` are included and defined in the Python-esque language, it could be argued that these should be `KEYWORD` tokens. However, they are indeed `IDENTIFIER` tokens as they are names of functions, rather than directives that change the control flow of the program, and you could still create variables called `input` or `print` if you wanted!

Since this language is sensitive to indentations, you can also see that there are `INDENT` and `DEDENT` tokens, which help the compiler to group blocks of code together later on. If you were to remove these tokens, there wouldn't be any other indicator to tell if an `if` keyword should run _if_ another `if` statement runs, or after which `if` keyword should an `else` keyword run!

I hope this has been an interesting read about the first stage of compiling a program, and in the next post, we will go over syntax analysis!
