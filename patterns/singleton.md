# Singleton

### Instance in Static property:

```sh
function Uniq() {
	if (typeof Uniq.instance === 'object') {
		return Uniq.instance;
    }
	
	this.someProp = true;

	Uniq.instance = this;
}
```

### Instance in closure v. 1:

```sh
function Uniq() {
	let instance = this;
	this.someProp = true;

	Uniq = function() {
		return instance;
    }
}
```

### Instance in closure v. 2:

```sh
let Uniq;

(function() {
	let instance;
	
	Uniq = function Uniq() {
		if(instance) {
			return instance;
        }
	
		instance = this;

		this.someProp = true;
    }
})();
```

### Test cases: 

```sh
Uniq.prototype.nothing = true;
let uni1 = new Uniq();

Uniq.prototype.everything = true;
let uni2 = new Uniq();


uni1 === uni2;															// true

uni1.nothing && uni1.everything && uni2.nothing && uni2.everything; 	// true

uni1.constructor == Uniq; 												// true
```