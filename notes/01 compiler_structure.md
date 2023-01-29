# Structure of  Compilers



1. [Lexical Analysis](./03%20lexical_analysis.md)

   Dividing input texts "tokens"

   - < token class , substring >
   
   
   
2. [Parsing](./04%20top-down%20parsing.md)

   Generates a parsing tree

   ```C++
   if (x == y) x = 10; else x = 11;
   ```

   

3. [Semantic Analysis](./06%20semantic-analysis.md)

   Compilers do limited semantic analysis to catch inconsistencies

   Programming languages define strict rules to avoid semantic ambiguities

   

   Type mismatch: the usage of a variable does not match its type

   

4. Optimisation

   Makes programme run faster and use less memory

   ```c++
   int x = y * 0;
   int x = 0;
   // this optimisation is valid ONLY if "y" is a number
   ```

   

5. Code Generation

   Converts programme into Assembly code
