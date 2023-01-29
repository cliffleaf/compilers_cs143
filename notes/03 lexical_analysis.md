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

