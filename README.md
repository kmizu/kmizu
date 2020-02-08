# kmizu

A programming language executed by me.  It is experimentation about a programming language which interpreter is a human (expecially myself).

## Concrete Syntax

Omitted.  Parsed by myself

## Abstract Syntax

```
// I is an idenfitier

T = Int
  | Boolean

S = if E S S                // if statement
  | while E S               // for statement
  | declare T I E           // variable declaraion
  | expression E            // expression statement
  | assignm I E             // assignment 
  | block [S]               // block
     
E = add E E
  | subtract E E
  | multiply E E
  | divide E E
  | lte E E
  | lt E E
  | gte E E
  | gt E E
  | L

L = (integer literal)
  | (boolean literal)
```
  
## Typing Rule

Omitted.  Typed by myself

## Operational Semantics

Omitted.  It is pseudo-code of an kmizu interpreter.

```scala
def execute(x, env) = {
  x match {
    case tree.if(cond, then, else) =>
      if(eval(cond, env)) execute(then, env) else execute(else, env)
    case tree.while(cond, body) =>
      while(eval(cond, env)) execute(body, env)
    case tree.declare(_, id, init) =>
      env.put(id, eval(init))
    case tree.assign(id, expr) =>
      env.put(id, eval(expr))
    case tree.block(elements) =>
      for(e <- elements){
        execute(e, env)
      }
  }
}
def eval(x, env) = {
  x match {
    case tree.add(x, y) =>
      eval(x, env) + eval(y, env)
    case tree.subtract(x, y) =>
      eval(x, env) - eval(y, env)
    case tree.multiply(x, y) =>
      eval(x, env) * eval(y, env)
    case tree.divide(x, y) =>
      eval(x, env) * eval(y, env)
    case tree.lt(x, y) =>
       eval(x, env) < eval(y, env)
    case tree.lte(x, y) =>
       eval(x, env) <= eval(y, env)
     case tree.gt(x, y) =>
       eval(x, env) > eval(y, env)
     case tree.gte(x, y) =>
       eval(x, env) >= eval(y, env)       
    case tree.integer(v) =>
      v
    case tree.boolean(v) =>
      v
  }
}
```
