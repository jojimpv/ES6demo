# ES6demo

## Array Helper methods:

### forEach

* An anonymous function (Iterator) is passed in `forEach` for action on each element

colors = ["red", "blue", "green"]
colors.forEach(function(color){
    console.log(color);
})
* May not change the orginal array. Just some actions using iteration over array

### map

* An anonymous function (Iterator) is passed in to `map` and it retuns an element.
* Output is array of same length as input

### filter

* An anonymous function (Iterator) is passed in to `filter` and it retuns true or false for each element.
* Output is an array of length >= 0

### find

* An anonymous function (Iterator) is passed in to `find` and it retuns true or false for each element. 
  The first element returned true will be the output of `find`
* Output is an element from array or undefined if none found

### every & some 

* An anonymous function (Iterator) is passed in to `every` and it retuns true or false for each element. 
  The first element returned true will be the output of `find`
* Output is boolean

### reduce

* An anonymous function (Iterator) is passed in to `reduce` which accept two arguments say (prev, element) it need to return new value of prev. The new prev will be used for next element and so on. 


## const/let

* const - for immutable vars
* let - for muttable vars

## String templates

* String templates denoted by back quotes can be used for expressions with `${}`

## Arrow functions
const fn = (arg1, arg2) => {return arg1 + arg2}
* if only one argument, avoid paranthesis around it
* if simple expression, avoid curly brackets 

## Enhanced object litterals

{
    data,
    fn(){
        return this.data;
    }
}

* Note 'data' insted of 'data: data'
* Note 'fn' instread of 'fn: function(){..}'

## Default function argumets 
fn(data, url, method='GET')

* If 'method' is `undefined`, then it will get value as 'GET'
* If menthod is `null`, then it will be `null` itself

## Rest and spread operator

* `fn(...rest)` to accept a list of positional arguments
*  `inner_fn(...rest)` to pass all vars from outer

## Destructuring 

{type} = expence;  // expence is an object, destructure property from object
[ company1 ] = companies;  // companies is an array, destructure element from array
[ company1, ...rest ] = companies;
[ {length} ] = companies;  // length of first company  
* Note we have an `=` in the expression

## Class

class Car(){
    constructor(options){
        this.name = options.name
    }
    run(){
        console.log('running..')
    }
}

class Tayota extends Car {
    constructor(options){
        super(options);
    }
    horn(){
        console.log('beep..')
    }
}

tayota = new Tayota({name:'Naew car'});
tayota.run();
tayota.horn();

## Generators

EngTeam = {
    size: 3,
    lead: 'Man1',
    manager: 'Man2',
    techie: 'Man3'
}

function* EngTeamIter(team){
    yield team.lead;
    yield team.manager;
    yield team.techie;
}

names = []
for (let i of EngTeamIter(EngTeam)) {
    names.push(i)
}
console.log(names)

// For default iter

EngTeam = {
    size: 3,
    lead: 'Man1',
    manager: 'Man2',
    techie: 'Man3',
    [Symbol.iterator]: function* () {
        yield this.lead,
        yield this.manager,
        yield this.techie
    }
}

## Promises and fetch

url = "https://jsonplaceholder.typicode.com/posts"

fetch(url)
    .then(response => response.json())
    .then(data => console.log(data));