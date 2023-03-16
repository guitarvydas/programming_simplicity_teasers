
# Creating a DSL



Hints: 
- COPY/PASTE the above DSL into an example section of the Ohm-Editor, then see if you can create a grammar that groks this DSL.
- A fabrication string is any set of characters between the pairs of quotes ‛...’.  You don't need to parse the stuff inside of the string, as long as you write a pattern that begins with ‛ and ends with ’ and you recognize parameter names bracketed by «...».
- If literal `$` characters appear in the fabrication string, you will need to escape them, to keep JavaScript from complaining.
