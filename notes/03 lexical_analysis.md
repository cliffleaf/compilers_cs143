# Lexical Analysis

```c++
if (x == y)
	return z;

// A compiler would see it as
// \tif (i == j)\n\t\treturn z;
```



## Token Classes

Identifier: strings of letters or digits, starting with a letter

Integer: non-empty string of digits

Keyword: system-preserved words

Whitespace: non-empty sequence of blanks, new lines and tabs

Syntaxes like ``(`` , ``)``, ``;`` , ``=`` are token classes by themselves



## Purpose of Lexical Analysis

- Recognise substrings (lexeme) of the input programme
- Identify the token class of each lexeme. Each token is a tuple of `` < class , lexeme > `` 
- Communicate tokens to the parsers



Lookahead: we scan the code from left to right, but sometimes the meaning of a substring depends on what is coming next

- Also where does a token end e.g. is it ``=`` or ``==``



## Regular Language

Specify which set of strings is in a token class



Components of regular language

- Union: $$A+B=\{a|a\in A\} \cup \{b|b\in B\}$$

- Concatenation: $$AB=\{ab|a\in A\ and\ b\in B\}$$
- Iteration: $$A*=AAA......$$



Five Constructs

- Two base cases - $$\epsilon$$ and 1-character strings
- Three compound expressions - union, concatenation, iteration
