# Lexical Analysis

```c++
if (x == y)
	return z;

// A compiler would see it as
// \tif (i == j)\n\t\treturn z;
```



## Token Classes

**Identifier**: non-empty string of letters or digits, starting with a letter

**Integer**: non-empty string of digits

**Keyword**: system-preserved words

**Whitespace**: non-empty sequence of blanks, new lines and tabs

Syntaxes like ``(`` , ``)``, ``;`` , ``=`` are token classes by themselves



## Purpose of Lexical Analysis

- Recognise substrings (lexeme) of the input programme
- Identify the token class of each lexeme. Each token is a tuple of `` < class , lexeme > `` 
- Communicate tokens to the parsers



**Lookahead**: we scan the code from left to right, but sometimes the meaning of a substring depends on what is coming next

- Also where does a token end e.g. is it ``=`` or ``==``



## Regular Language

Specify which set of strings is in a token class



Components of regular language

- Union: $$A+B=\{a|a\in A\} \cup \{b|b\in B\}$$

- Concatenation: $$AB=\{ab|a\in A\ and\ b\in B\}$$
- Iteration: $$A*=AAA......$$



Five Constructs

- Two base cases --- $$\epsilon$$ and 1-character strings
- Three compound expressions - union, concatenation, iteration



## Formal Language

$$L:expression\rightarrow set\ of\ strings$$

<img src="C:\Users\kevin\Development\Compilers\notes\img\formal language.jpg" alt="formal language" style="zoom: 67%; float: left;" />



Why use a meaning function

- Makes clear distinction between syntax and semantics
- Consider notations as a separate issue

- Expressions (syntax) and meanings (semantics) are not 1-1 mapping



## Lexical Specifications

Define token classes using the definition of formal language

Integer: non-empty string of digits

```c++
// digit digit*
```

Identifier: non-empty string of letters or digits, starting with a letter

```c++
// letter (letter + digit)*
```

Whitespace: non-empty sequence of blanks, \n and \t

```c++
// (' ' + '\n' + '\t')(' ' + '\n' + '\t')*
// (' ' + '\n' + '\t')+
```



Below is a definition for token class ``number``

![num token class in Pascal](C:\Users\kevin\Development\Compilers\notes\img\num token class in Pascal.jpg)

##### Intuitive Algorithm

Let ``R`` be the construct of any acceptable language

Suppose input string $$x_1\ ...\ x_n$$

For $$1\le i\le n$$ do

1. Check if $$x_1\ ...\ x_i \in L(R)$$
2. If yes, remove $$x_1\ ...\ x_i$$ from input



##### Maximal Munch

Taking the algorithm above, and:

- $$x_1\ ...\ x_i \in L(R)$$
- $$x_1\ ...\ x_j \in L(R)$$
- $$i\neq j$$

In this case, we pick the longest substring to be the final expression



##### Priorities of Classification

1. If a word can both be an identifier and a keyword, then it is a keyword

2. $$x_1\ ...\ x_i \notin L(R)$$ Then it is ERROR

   But only mark it as ERROR if its previous strings are ERROR as well



## Finite Automata

Implement token classes using the definition of formal language



A finite automata consists of

- A set of states
- A set of accepted states
- A set of transitions

**$$\epsilon$$-closure**: The set of states that a state could go to with only $$\epsilon$$ transitions



1. Define the token classes using regular language
2. Map it into NFA then DFA
3. Map into 2D table - one dimension for state, other for input symbol, the cell records the resulting state

<img src="C:\Users\kevin\Development\Compilers\notes\img\implementing FA.jpg" alt="implementing FA" style="zoom:67%;" />



```c++
auto table = new int [row][col];
int i = 0;
int state = 0;
int next_symbol;

while (input[i]) {
    next_symbol = input[i++];
    state = table[state][next_symbol];
}
```



It is possible to optimise the table into 1-dimensional, taking advantage of the fact that some rows are duplicate

- 1D table where each column is the state
- Each state has a pointer to another array of states

<img src="C:\Users\kevin\Development\Compilers\notes\img\DFA table 1d.jpg" alt="DFA table 1d" style="zoom: 67%;" />
