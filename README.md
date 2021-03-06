## API
### Create New
#### Test Schema
```javascript
const Traversal = require("@marilyn.m/object-traversal");
const data = {
	candies: [
		{
			name: "Twizzler"
		}, 
		{
			name: "Skittles",
			type: "fruity"
		},
		{
			name: "Milky Way",
			type: "chocolate"
		},
	],
	drinks: [
		{
			name: "Champurrado",
			type: "chocolate"
		}
	]
};
const object_traversal = new Traversal(data);
```

### value()
get the final value when finished traversing the data.
	
### find(key:string)
Find the first occurrence of the key.
```javascript
/*
{ name: "Skittles", type: "fruity" }
*/
object_traversal.find("type").value();
```

### findAll(key:string)
```javascript
/*
[
	{ name: "Twizzlers" },
	{ name: "Skittles", type: "fruity" },
	{ name: "Milky Way", type: "chocolate" },
	{ name: "Champurrado", type: "chocolate" }
]
*/
object_traversal.findAll("name").value();
```

### findN(key:string, limit:number|null)
```javascript
/*
[
	{ name: "Twizzlers" },
	{ name: "Skittles", type: "fruity" },
	{ name: "Milky Way", type: "chocolate" },
]
*/
object_traversal.findN("name", 3).value();
```

### get(key:string)
```javascript
/*
[ "Twizzlers", "Skittles", "Milky Way', "Champurrado" ]
*/
object_traversal.get("name").value();
```

### first(key:string)
```javascript
/*
Twizzlers
*/
object_traversal.first("name").value();

/*
[ { name: "Champurrado", type: "chocolate" } ]
*/
object_traversal.first("drinks").value()
```

### where(key:string)
```javascript
/*
[
  { name: "Skittles", type: "fruity" },
  { name: "Milky Way", type: "chocolate" },
  { name: "Champurrado", type: "chocolate" }
]
*/
object_traversal.where("type").value()
```

### where(key:string, value:string)
```javascript
/*
[
  { name: "Milky Way", type: "chocolate" },
  { name: "Champurrado", type: "chocolate" }
]
*/
object_traversal.where("type", "chocolate").value()
```

### where(key:string, value:string, limit:string|null)
```javascript
/*
[
  { name: "Milky Way", type: "chocolate" },
]
*/
object_traversal.where("type", "chocolate", 1).value()
```


