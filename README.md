# Undoredo

This is the [*GridSound*](https://github.com/gridsound/daw)'s undoredo JavaScript implementation.

### Example

``` javascript
var undoredo = new Undoredo();

undoredo.onchange = function( obj ) {
  console.log( "onchange", obj );
};

undoredo.onassign = function( valuePath, val, previousValue ) {
  console.log( `onassign "${ valuePath }": ${ previousValue } -> ${ value }` );
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

// onassign "stock.diamond": 0 -> 5
// onassign "stock.gold": 0 -> 21
// onassign "stock.sapphire": undefined -> 1
// onchange {stock:{diamond:5,gold:21,sapphire:1}}

undoredo.undo();

// onassign "stock.diamond": 5 -> 0
// onassign "stock.gold": 21 -> 0
// onassign "stock.sapphire": 1 -> undefined
// onchange {stock:{diamond:0,gold:0,sapphire:undefined}}

undoredo.redo();

// onassign "stock.diamond": 0 -> 5
// onassign "stock.gold": 0 -> 21
// onassign "stock.sapphire": undefined -> 1
// onchange {stock:{diamond:5,gold:21,sapphire:1}}
```
