# ES8 Proposal: Static Constructor

## Introduction

A static constructor along with static members to a class allow shared data accessible from the class itself or instances.

## Rationale

The Singleton and Multiton patterns are two instances where this feature can be utilized.

## Syntax

A static constructor takes no members and is called before any instance or static method is used. The syntax for a static member is kind of a lazy suggestion here. Ideally this proposal should wait until public, private, static member syntax is well defined.

```js
class Multiton
{
    static constructor()
    {
        this.instances = {}; // instances is now static
    }
    constructor(name)
    {
        if (this.instances.hasOwnProperty(name))
        {
            throw `Multiton name already used`;
        }
        this.instances[name] = this;
    }
}

var foo = new Multiton(`foo`);
var bar = new Multiton(`bar`);
var baz = new Multiton(`bar`); // throws `Multiton name already used`
```
