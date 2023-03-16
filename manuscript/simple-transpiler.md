
# Creating a DSL


This would let us avoid writing JavaScript.  We could run the DSL to generate the above code, then COPY/PASTE the code into a JavaScript program.

What should the syntax for the DSL be?  Here's an untested suggestion:
```
SimpleFAB {
  Top [target eq v1 plus v2] = ‛
const semantics = g.createSemantics ().addOperation ("js", {
    Top (target, eq, v1, plus, v2) {
	return `
${«target».js()} = ${«v1».js()} + ${«v2».js()};
console.log (${target.js()});
`},
    _terminal () { return this.sourceString; }
});
’
}
```

Hints: 
- 'FAB' is a short-form for 'fabrication'.  
- Use non-ASCII quotes in pairs and non-ASCII brackets in pairs for easy matching by PEG-based parsers like Ohm-JS.
- COPY/PASTE the above DSL into an example section of the Ohm-Editor, then see if you can create a grammar that groks this DSL.
- A fabrication string is any set of characters between the pairs of quotes ‛...’.  You don't need to parse the stuff inside of the string, as long as you write a pattern that begins with ‛ and ends with ’ and you recognize parameter names bracketed by «...».
- If literal `$` characters appear in the fabrication string, you will need to escape them, to keep JavaScript from complaining.
