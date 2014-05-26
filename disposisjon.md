ECMAScript 6
============

## Arrow function
https://github.com/lukehoban/es6features#arrows
http://www.nczonline.net/blog/2013/09/10/understanding-ecmascript-6-arrow-functions/

Arrows are a function shorthand using the => syntax.
They are syntactically similar to the related feature in C#, Java 8 and CoffeeScript.
They support both expression and statement bodies.
Unlike functions, arrows share the same lexical this as their surrounding code.


- Lexical this binding
  - The value of this inside of the function is determined by where the arrow function is defined not where it is used.
- Not newable
  - Arrow functions cannot be used a constructors and will throw an error when used with new.
- Can’t change this
  - The value of this inside of the function can’t be changed, it remains the same value throughout the entire lifecycle of the function.

```Javascript
// Expression bodies
var odds = evens.map(v => v + 1);
var nums = evens.map((v, i) => v + i);

// Statement bodies
nums.forEach(v => {
  if (v % 5 === 0)
    fives.push(v);
});

// Lexical this
var bob = {
  _name: "Bob",
  _friends: [],
  printFriends() {
    this._friends.forEach(f =>
      console.log(this._name + " knows " + f));
  }
}
```


## Classes

http://dstrunk.com/ecmascript-6-features-classes/
http://code.tutsplus.com/articles/use-ecmascript-6-today--net-31582#class
http://wiki.ecmascript.org/doku.php?id=harmony:classes
https://github.com/lukehoban/es6features#classes
http://tc39wiki.calculist.org/es6/classes/

ES6 classes are a simple sugar over the prototype-based OO pattern.
Having a single convenient declarative form makes class patterns easier to use, and encourages interoperability.
Classes support prototype-based inheritance, super calls, instance and static methods and constructors.

    class SkinnedMesh extends THREE.Mesh {
      constructor(geometry, materials) {
        super(geometry, materials);

        this.idMatrix = SkinnedMesh.defaultMatrix();
        this.bones = [];
        this.boneMatrices = [];
        //...
      }
      update(camera) {
        //...
        super.update();
      }
      static defaultMatrix() {
        return new THREE.Matrix4();
      }
    }