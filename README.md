# Undoredo

This is the [*GridSound*](https://github.com/gridsound/daw)'s undoredo JavaScript implementation.

### Example

``` javascript
var undoredo = new Undoredo();

undoredo.onchange = function( actionObject, valuePath, value, previousValue ) {
  console.log( `onchange "${ valuePath }": ${ previousValue } -> ${ value }` );
};

undoredo.init( {
  stock: {
    diamond: 0,
    ruby: 0,
    gold: 0
  }
} );

undoredo.change( {
  stock: {
    diamond: 5,
    gold: 21,
    sapphire: 1
  }
} );

// onchange "stock.diamond": 0 -> 5
// onchange "stock.gold": 0 -> 21
// onchange "stock.sapphire": undefined -> 1

undoredo.undo();

// onchange "stock.diamond": 5 -> 0
// onchange "stock.gold": 21 -> 0
// onchange "stock.sapphire": 1 -> undefined (deleted)

undoredo.redo();

// onchange "stock.diamond": 0 -> 5
// onchange "stock.gold": 0 -> 21
// onchange "stock.sapphire": undefined -> 1
```
