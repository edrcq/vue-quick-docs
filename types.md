# Les types en JS
  
La plus part des developpeurs diront qu'il n'y a pas de type dans un language dynamique comme JS. Voyons voir ce que nous dit la spécification du language ECMAScript 5.1 (http://www.ecma-international.org/ecma-262/5.1/)

> Algorithms within this specification manipulate values each of which has an associated type. The possible value types are exactly those defined in this clause. Types are further subclassified into ECMAScript language types and specification types.  
An ECMAScript language type corresponds to values that are directly manipulated by an ECMAScript programmer using the ECMAScript language. The ECMAScript language types are Undefined, Null, Boolean, String, Number, and Object.

Si vous êtes fan de languages fortement typé, Vous pourriez dire que le mot "type" n'est pas approprie ici. Dans ces languages, le mot "type" signifie bien plus que ce qu'il signifie en JS.

## Liste des types

JavaScript defines seven built-in types:

* `null`
* `undefined`
* `boolean`
* `number`
* `string`
* `object`
* `symbol` -- ajouté dans ES6!

```js
typeof undefined     === "undefined"; // true
typeof true          === "boolean";   // true
typeof 42            === "number";    // true
typeof "42"          === "string";    // true
typeof { life: 42 }  === "object";    // true
```

Le type `null` a éte exclus de la liste précedente car il est un peu 'buggé' dans le sens où:
```js
typeof null === "object"; // true
```

Il est facile de pensé que les `fonctions` sont des types primitifs également.
Les `function` malgrés le fait qu'elle vous renvoient un type `function`
```js
typeof function a(){ /* .. */ } === "function"; // true
```

Sont en réalité un sous-type d'Object. Ce sont des `callable object`, (des objets invocables).
Ces objets ont une propriété `[[Call]]` qui leurs permettent d'être invoqués.

Le fait que les functions soit des objets, est en réalité très utile. Exemple:

```js
function a(b,c) {
	/* .. */
}

a.length; // 2
```



### Conclusion
JavaScript a sept types intégrés: `null`, `undefined`, boolean, number, string, object, symbol. Ils peuvent être identifiés par `typeof`

Les variables n'ont pas de types, mais leurs valeurs en ont. Ces types définissent le comportement intrinsèque des valeurs.

De nombreux développeurs supposeront que "non défini" et "non déclaré" sont à peu près la même chose, mais en JavaScript, ils sont assez différents. undefined est une valeur qu'une variable déclarée peut contenir. "Non déclaré" signifie qu'une variable n'a jamais été déclarée.

JavaScript confond malheureusement ces deux termes, non seulement dans ses messages d'erreur ("ReferenceError: a is not defined") mais aussi dans les valeurs de retour de typeof, qui est "indéfini" dans les deux cas.

Cependant, la sécurité (empêchant une erreur) sur `typeof` lorsqu'il est utilisé contre une variable non déclarée peut être utile dans certains cas.

```js
// oops, this would throw an error!
if (DEBUG) {
	console.log( "Debugging is starting" );
}

// this is a safe existence check
if (typeof DEBUG !== "undefined") {
	console.log( "Debugging is starting" );
}
```

#### Credits
YDKJS
