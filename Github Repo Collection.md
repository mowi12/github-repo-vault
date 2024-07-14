--- start-multi-column: Header
```column-settings  
number of columns: 2
border: off  
```

> [Link to Github Stars](https://github.com/stars/mowi12)

--- end-column ---

```dataviewjs
//const pages = dv.pages('"Github Repo Collection/Repos"')
let pages = dv.pages('#repo and -"Templates"')
let count = pages.length

dv.paragraph("Total Stars: " + count)
```

--- end-multi-column

```dataviewjs
//const pages = dv.pages('"Github Repo Collection/Repos"')
let pages = dv.pages('#repo and -"Templates"')
	.filter(p => { // name filtering
		return true // comment out to filter
		
		if (p.name.toLowerCase().startsWith("a", 1)) {
			return true
		}
	})
	.filter(p => { // name filtering
		return true // comment out to filter
		
		if (p.name.toLowerCase().includes("a")) {
			return true
		}
	})
	.filter(p => { // description filtering
		return true // comment out to filter
		
		if (p.description.toLowerCase().includes("full-stack")) {
			return true
		}
	})
	.filter(p => { // tag filtering
		//return true // comment out to filter
		
		for (const tag of p.tags) {
			if (tag.toLowerCase() === "markdown") {
				return true
			}
		}
	})
	.filter(p => { // precise tag filtering
		return true // comment out to filter
		
		for (const tag of p.tags) {
			if (tag.toLowerCase().includes("gui")) {
				return true
			}
		}
	})
	.filter(p => { // precise link filtering
		return true // comment out to filter
		
		for (const tag of p.tags) {
			if (tag.toLowerCase().includes("gui")) {
				return true
			}
		}
	})
	.sort(p => p.name)
	.map(p => [p.file.link, p.name, p.description, p.tags])

dv.table(["Name", "Link to Github", "Description", "Tags"], pages)
```