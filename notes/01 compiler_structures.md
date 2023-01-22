## Structure of  Compilers

1. [Lexical Analysis](./02%20lexical_analysis.md)

   Dividing texts into "words" and "tokens"

   - Tokens: language-preserved keywords and syntaxes. 
   - Words: user-defined variables

   

2. [Parsing](./03%20top-down%20parsing.md)

   Generates a parsing tree

   ```C++
   if (x == y) x = 10; else x = 11;
   ```

   

3. [Semantic Analysis](./05%20semantic-analysis.md)

   Compilers do limited semantic analysis to catch inconsistencies

   Programming languages define strict rules to avoid semantic ambiguities

   

   Type mismatch: the usage of a variable does not match its type

   

4. Optimisation

   Makes programme run faster and use less memory

   ```c++
   int x = y * 0;
   int x = 0;
   // this optimisation is valid ONLY when "y" is a number
   ```

   

5. Code Generation

   Converts programme into Assembly code

[./"02 lexical_analysis"]: 
[./"02 lexical_analysis.md"]: 
["./lexical_analysis.md"]: 