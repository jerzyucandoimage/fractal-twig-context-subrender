# Extended Fractal Twig Adapter

An adapter that extends the [Fractal Twig](https://github.com/frctl/twig) adapter and introduces `include` operator in 
context data.

## Installation

```bash
npm install --save-dev https://github.com/jerzyucandoimage/fractal-twig-context-subrender.git
```

in your `fractal.js`

```js
const fractal = require('@frctl/fractal').create();
const twigAdapter = require('fractal-twig-context-subrender');
const twig = twigAdapter();
```

in the fractal configuration file

```js
supportIncludesInTheContextData: true
```
<br/>

## The `include` statement 



### To include all the data from another component and assign it to specific variable

```yaml
context: 
  include: 'component-name--variant-name as customVariableName'   
```

### To include object by it's source path

```yaml
context: 
  someDestinationObject:
    include: 'component-name--variant-name.path.to.the.source.data.object'   
```

### To include all object's sub-properties use the `spread ... ` operator

```yaml
context: 
  someDestinationObject:
    include: '...component-name--variant-name'   
```

### To include all object's sub properties - spread operator with source path

```yaml
context: 
  someDestinationObject:
    include: '...component-name--variant-name.some.path'   
```

### To include multiple entries at once

```yaml
context: 
  someDestinationObject:
    include: 'component-name--variant-name.some.path as someCustomVariableName, component-name--variant-name.some.path as anotherCustomVariableName'   
```

### To include multiple entries one by one

```yaml
context: 
  someDestinationObject:
    include1: 'component-name--variant-name.some.path as someCustomVariableName'
    include2: 'component-name--variant-name.some.path as anotherCustomVariableName'  
```

### By default existing variables are not being overriden. To force overriding use `!` operator at the end

```yaml
context: 
  someDestinationObject:
    include: 'component-name--variant-name.some.path!'   
```

```yaml
context: 
  someDestinationObject:
    include: '...component-name--variant-name.some.path!'   
```

```yaml
context: 
  someDestinationObject:
    include: 'component-name--variant-name.some.path as customVariableName!'   
```
