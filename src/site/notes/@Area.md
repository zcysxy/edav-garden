---
{"dg-publish":true,"permalink":"/area/","title":"Areas","created":"2021-08-17T21:58:15","updated":"2023-03-29T00:40:27"}
---

> [!meta]-
> sup:: [[@\|@]]  
> state:: done  

# 🌐 Areas

```dataviewjs-hold
// Helper function to remove duplicate links
let unique = function(array) {
	const unique_set = [...new Set(array.map(s => String(s)))];
    return Array.from(unique_set)
}
dv.table(["banner", "link", "related"],
	dv.pages('-"templates"')
	.where(p => p.type === "index" && p.banner) // Index notes with a banner
 	.sort(p => p.file.inlinks.length, 'desc')
	.map(p => [
		"![](" + p.banner + ")",
		p.banner_icon + " " + p.file.link,
  		// Show most related notes
        unique(p.file.inlinks.filter(s => (dv.page(s) && dv.array(dv.page(s).sup).some(u => dv.equal(u,p.file.link))))
        			   		 .sort(s => -dv.page(s).file.inlinks.length)
                  			 .map(s => dv.page(s).file.link)
        ).splice(0,5).join(" ")
	])
)
```

```expander
"[[@Area]]" -file:(@)
```

* [[Computer Science\|Computer Science]]
    * [[Algorithm\|Algorithm]]
    - [[Database\|Database]]
    - [[Artificial Intelligence\|Artificial Intelligence]]
    - [[Deep Learning\|Deep Learning]]
    - [[Reinforcement Learning\|Reinforcement Learning]]
    - [[Data Structure\|Data Structure]]
    - [[Language\|Language]]
        - [[SQL\|SQL]]
        - [[Python\|Python]]
        - [[Lua\|Lua]]
        - [[MATLAB\|MATLAB]]
        - [[R\|R]]
        - [[JavaScript\|JavaScript]]
        - [[Shell Script\|Shell Script]]
        - [[HTML\|HTML]]
        - [[CSS\|CSS]]
        - [[LaTeX\|LaTeX]]
* [[Math\|Math]]
    * [[Probability Theory\|Probability Theory]]
    * [[Numerical Linear Algebra\|Numerical Linear Algebra]]
    * [[Optimization\|Optimization]]
* [[汉语\|汉语]]
    * [[宋词\|宋词]]
* [[Knowledge Management\|Knowledge Management]]
    * [[Productivity\|Productivity]]
    * [[Notetaking\|Notetaking]]
* [[Poetry\|Poetry]]
* [[English\|English]]
* [[Political Philosophy\|Political Philosophy]]
 
<!-- expand end -->
