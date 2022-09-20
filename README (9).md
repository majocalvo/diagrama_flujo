# Desafío: javaScript

## Nombre de Desafío: introduccion_js

## Instrucciones

Determiná que será impreso en la consola, sin ejecutar el código.

> Investiga cuál es la diferencia entre declarar una variable con `var` y directamente asignarle un valor.

// Las diferencias son:
1. Las variables declaradas se limitan al contexto de ejecución en el cual son declaradas. Las variables no declaradas siempre son globales.

2. Las variables declaradas son creadas antes de ejecutar cualquier otro código. Las variables sin declarar no existen hasta que el código que las asigna es ejecutado.

3. Las variables declaradas son una propiedad no-configurable de su contexto de ejecución (de función o global). Las variables sin declarar son configurables (p. ej. pueden borrarse).



```javascript
x = 1;
var a = 5;
var b = 10;
var c = function(a, b, c) {
  var x = 10;
  console.log(x); //10
  console.log(a); //8
  var f = function(a, b, c) {
    b = a;
    console.log(b); //8
    b = c;
    var x = 5;
  }
  f(a,b,c);
  console.log(b); //9
}
c(8,9,10);
console.log(b); //10
console.log(x);//1
```

```javascript
console.log(bar); //undefined
console.log(baz); //2

foo(); //Hola!
function foo() { 
   console.log('Hola!'); 
}

var bar = 1;
baz = 2;

```

```javascript
var instructor = "Jhoswe";
if(true) {
    var instructor = "Jose";
} 
console.log(instructor); //Jose
```

```javascript
var instructor = "Jhoswe";
console.log(instructor); //Jhoswe
(function() {
   if(true) {
      var instructor = "Jose";
      console.log(instructor); //Jose
})();
console.log(instructor); //Jose
```

```javascript
var instructor = "Jhoswe";
let pm = "Jose";
if (true) {
    var instructor = "The Flash";
    let pm = "Reverse Flash";
    console.log(instructor); //"The Flash"
    console.log(pm); // "Reverse Flash"
}
console.log(instructor); //"The Flash"
console.log(pm); // "Jose"
```
### Coerción de Datos

¿Cuál crees que será el resultado de la ejecución de estas operaciones?:

```javascript
6 / "3"  //2
"2" * "3" //6
4 + 5 + "px" //9px
"$" + 4 + 5 // $45
"4" - 2 // 2
"4px" - 2 // NaN
7 / 0 // Infinity
{}[0]  // Undefined
parseInt("09") // 9
5 && 2 //2
2 && 5 // 5
5 || 0  // 5
0 || 5 // 5
[3]+[3]-[10]  //23
3>2>1    //false
[] == ![] //true
```

> Si te quedó alguna duda repasá con [este artículo](http://javascript.info/tutorial/object-conversion).


### Hoisting

¿Cuál es el output o salida en consola luego de ejecutar este código? Explicar por qué:

```javascript
function test() {
   console.log(a);
   console.log(foo());

   var a = 1;
   function foo() {
      return 2;
   }
}

test(); //undefined}
        //  2

El primer valor es "undefined", ya que la variable está definida de manera posterior al console.log y no está inicializada.
El segundo valor es "2", ya que la función foo está declarada y aplica el hoisting, por lo tanto al leer el código la función foo se declara al comienzo.
```

Y el de este código? :

```javascript
var snack = 'Meow Mix';

function getFood(food) {
   
   if (food) {
        var snack = 'Friskies';
        return snack;
    }
    return snack;
}

getFood(false); //undefined.

No está definido en la función qué valor traer para el caso de que food=false.
```


### This

¿Cuál es el output o salida en consola luego de ejecutar esté código? Explicar por qué:

```javascript
var fullname = 'Jhoswe Castro';
var obj = {
   fullname: 'Jose Zuñiga',
      fullname: 'Jorge Alonso',
      getFullname: function() {
         return this.fullname;
      }
   };

console.log(obj.prop.getFullname()); Undefined

var test = obj.prop.getFullname;

console.log(test()); Undefined
```

Es undefined porque no hay definido un prop.

### Event loop

Considerando el siguiente código, ¿Cuál sería el orden en el que se muestra por consola? ¿Por qué?

```javascript
function printing() {
   console.log(1);
   setTimeout(function() { console.log(2); } , 1000);
   setTimeout(function() { console.log(3); } , 0);
   console.log(4);
}

printing(); // 1,4,3,2

Toma primero el orden de las console.log y luego toma la función settimeout y los ordena según los segundos de espera.
```
