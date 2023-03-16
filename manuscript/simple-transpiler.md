
# Creating a DSL

For starters, the goal should be to emit code that looks like
```
const semantics = g.createSemantics ().addOperation ("js", {
    Top (target, eq, v1, plus, v2) {
	return `
${target.js()} = ${v1.js()} + ${v2.js()};
console.log (${target.js()});
`},
    _terminal () { return this.sourceString; }
});
```

