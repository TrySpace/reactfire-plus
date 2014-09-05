# ReactFire-Plus

This is a ReactFire fork [https://github.com/firebase/reactfire]

No hard changes, only the addition of a 3rd argument as an array: [ once, type, eventType ]
`once`: boolean to invoke .once() on a firebaseRef, instead of .on()
`type`: either 'state' or 'props', to bind to (**Props will not bind with .on(), for it is bad practice**. `props` will only work when `once` is `true` )
`eventType`: must be valid Firebase eventType strings: 'value', 'child_added', 'child_changed', 'child_removed', or 'child_moved'

And for some shorthands for various combinations of the above, see below:

## Install

Just replace the reactfire.js file

## API Reference

For original documentation: [https://github.com/firebase/reactfire]

## API Additions

### bindOnAdded(firebaseRef, bindVar, asArray)

Creates a 'child_added' binding between Firebase and the inputted bind variable as an Object if `isArray` not specified, as an Array if `isArray === true`.
```javascript
this.bindOnAdded( new Firebase('https://<YOUR_FIREBASE>/'), 'items'); // bind as Object
```

### bindOnRemoved(firebaseRef, bindVar, asArray)

Creates a 'child_removed' binding between Firebase and the inputted bind variable as an Object if `isArray` not specified, as an Array if `isArray === true`.
```javascript
this.bindOnRemoved( new Firebase('https://<YOUR_FIREBASE>/'), 'items');
```

### bindOnChanged(firebaseRef, bindVar, asArray)

Creates a 'child_changed' binding between Firebase and the inputted bind variable as an Object if `isArray` not specified, as an Array if `isArray === true`.
```javascript
this.bindOnChanged( new Firebase('https://<YOUR_FIREBASE>/'), 'items');
```
### bindOnMoved(firebaseRef, bindVar, asArray)

Creates a 'child_moved' binding between Firebase and the inputted bind variable as an Object if `isArray` not specified, as an Array if `isArray === true`.
```javascript
this.bindOnMoved( new Firebase('https://<YOUR_FIREBASE>/'), 'items');
```

### onceAsArray(firebaseRef, bindVar, [ type, eventType ])

Creates a one-time exchange between Firebase and the inputted bind variable as an Array.  Defaults to type 'state' and eventType 'value'
```javascript
this.onceAsArray( new Firebase('https://<YOUR_FIREBASE>/'), 'items', [ 'props', 'child_removed' ] );
```

### onceAsObject(firebaseRef, bindVar, [ type, eventType ])

Creates a one-time exchange between Firebase and the inputted bind variable as an Object. Defaults to type 'state' and eventType 'value'
```javascript
this.onceAsObject( new Firebase('https://<YOUR_FIREBASE>/'), 'items', [ 'props', 'child_removed' ] );
```

### propAsArray(firebaseRef, bindVar, [ eventType ])

Creates a one-time props exchange between Firebase and the inputted bind variable as an Array. Defaults to eventType 'value'
```javascript
this.propAsArray( new Firebase('https://<YOUR_FIREBASE>/'), 'items', [ 'child_removed' ] );
```

### propAsObject(firebaseRef, bindVar, [ eventType ])

Creates a one-time props exchange between Firebase and the inputted bind variable as an Array. Defaults to eventType 'value'
```javascript
this.propAsObject( new Firebase('https://<YOUR_FIREBASE>/'), 'items', [ 'child_removed' ] );
```

## Additional options
### bindAsArray(firebaseRef, bindVar, options[ once, type, eventType ])

Creates a binding between Firebase and the inputted bind variable as an array. The Firebase
reference will be stored in `this.firebaseRefs[bindVar]`.

```javascript
var firebaseRef = new Firebase("https://<YOUR_FIREBASE>/");
this.bindAsArray(firebaseRef, "items" [ false, 'props', 'child_removed' ]);
```

### bindAsObject(firebaseRef, bindVar, options[ once, type, eventType ])

Creates a binding between Firebase and the inputted bind variable as an object. The Firebase
reference will be stored in `this.firebaseRefs[bindVar]`.

```javascript
var firebaseRef = new Firebase("https://<YOUR_FIREBASE>/");
this.bindAsObject(firebaseRef, "items", [ false, 'props', 'child_removed' ]);
```

## Fork it!

Go ahead, do it!