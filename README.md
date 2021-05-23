# Complete JavaScript Interview Questions & Answers

> Click :star:if you like the project. Pull Requests are highly appreciated. Follow
> [@iamtalvinder](https://www.linkedin.com/in/iamtalvinder/) for more frontend insights.

### Table of Contents

| No. | Questions                                                                                           |
| --- | --------------------------------------------------------------------------------------------------- |
| 1   | [What are the primitive data types in javascript](#what-are-the-primitive-data-types-in-javascript) |
| 2   | [What is the symbol data type](#what-is-the-symbol-data-type)|
| 3   | [What is the difference between null and undefined](#what-is-the-difference-between-null-and-undefined)| 
| 4   | [What are sets in javascript ?](#what-are-sets-in-javascript)
| 5   | [How to remove duplicate values from an array](#how-to-remove-duplicate-values-from-an-array)
| 6   | [What are generator functions](#what-are-generator-functions)
| 7   | [What are arrow functions in ES6](#what-are-arrow-functions-in-es6)

1. ### What are the primitive data types in javascript

   These six types are considered to be primitives. A primitive is not an object and has no methods
   of its own. All primitives are immutable.

    1. **String:** Collection of characters i.e words.

    2. **Number:** integers, floats, etc.

    3. **Boolean** true or false

    4. **Null** it represents no value. However, the typeof(null) is an object in javascript/

    5. **Undefined** a declared variable but hasn’t been given a value.

    6. **Symbol** a unique value that's not equal to any other value.

-----
2. ### What is the symbol data type

    The JavaScript ES6 introduced a new primitive data type called Symbol. Symbols are immutable (cannot be changed) and are unique. For example -

    ```javascript
    // two symbols with the same description

    const value1 = Symbol('hello');
    const value2 = Symbol('hello');

    console.log(value1 === value2); // false
    ```

    Though value1 and value2 both contain the same description, they are different.
    -----

    #### Creating Symbol

    Use the Symbol() function to create a Symbol. For example -

    ```javascript
    // creating symbol
    const z = Symbol()
    typeof z; // symbol
    ```
    Type of a symbol is a symbol.

    You can pass an optional string as its description.

    ```javascript
    const z = Symbol('hello');
    console.log(z); // Symbol(hello)
    console.log(z.description); // hello
    ```
    -----
    #### Add Symbol as an Object Key
    You can add symbols as a key in an object using square brackets []. For example -

    ```javascript
    let id = Symbol("id");

    let person = {
        name: "John",

        // adding symbol as a key
        [id]: 123 // not "id": 123
    };

    console.log(person); // {name: "John", Symbol(id): 123}
    ```

    Note: Symbols are not included in for...in Loop

    -----
    #### So what is the benefit of using symbol ?

    If the same code is used multiple times, then it is better to use Symbols in the object key. It's because you can use the same key name in different codes and avoid duplication issues. For example -

    ```javascript
    let person = {
        name: "Jack"
    };

    // creating Symbol
    let id = Symbol("id");

    // adding symbol as a key
    person[id] = 23; 
    ```

    In the above program, if the person object is also used by another program, then you wouldn't want to add a property that can be accessed or changed by another program. Hence by using Symbol, you create a unique property that you can use.

-----

3. ### What is the difference between null and undefined

    In JavaScript, undefined means a variable has been declared but has not yet been assigned a value, such as:

    ```javascript
    var testVar;
    console.log(testVar); //shows undefined
    console.log(typeof testVar); //shows undefined
    ```

    null is an assignment value. It can be assigned to a variable as a representation of no value:

    ```javascript
    var testVar = null;
    console.log(testVar); //shows null
    console.log(typeof testVar); //shows object
    ```

    You may wonder why the typeof returns 'object' for a value that is null. This was actually an error in the original JavaScript implementation that was then copied in ECMAScript. Today, it is rationalized that null is considered a placeholder for an object, even though, technically, it is a primitive value."

-----

4. ### What are sets in javascript

    The Set object lets you store unique values of any type, whether primitive values or object references.

    ```javascript
    const mySet1 = new Set()

    mySet1.add(1)           // Set [ 1 ]
    mySet1.add(5)           // Set [ 1, 5 ]
    mySet1.add(5)           // Set [ 1, 5 ]
    mySet1.add('some text') // Set [ 1, 5, 'some text' ]
    const o = {a: 1, b: 2}
    mySet1.add(o)

    mySet1.add({a: 1, b: 2})   // o is referencing a different object, so this is okay

    mySet1.has(1)              // true
    mySet1.has(3)              // false, since 3 has not been added to the set
    mySet1.has(5)              // true
    mySet1.has(Math.sqrt(25))  // true
    mySet1.has('Some Text'.toLowerCase()) // true
    mySet1.has(o)       // true

    mySet1.size         // 5

    mySet1.delete(5)    // removes 5 from the set
    mySet1.has(5)       // false, 5 has been removed

    mySet1.size         // 4, since we just removed one value

    console.log(mySet1)
    // logs Set(4) [ 1, "some text", {…}, {…} ] in Firefox
    // logs Set(4) { 1, "some text", {…}, {…} } in Chrome
    ```

-----

5. ### How to remove duplicate values from an array

    Using the Set constructor and the spread syntax:

    ```javascript
    uniq = [...new Set(array)];
    ```

    for example  -
    ```javascript
    let arr = [1,2,1,1,4,6,3,5,2,6,5];
    console.log([...new Set(arr)]);     //console.log([...new Set(arr)])
    ```    

-----

6. ### What are generator functions

    Regular functions return only one, single value (or nothing).

    Generators can return (“yield”) multiple values, one after another, on-demand. They work great with iterables, allowing to create data streams with ease. To create a generator, we need a special syntax construct: function*, so-called “generator function”.

    ```javascript
    function* generateSequence() {
    yield 1;
    yield 2;
    return 3;
    }
    ```

    Generator functions behave differently from regular ones. When such function is called, it doesn’t run its code. Instead it returns a special object, called “generator object”, to manage the execution.

    ```javascript
    function* generateSequence() {
    yield 1;
    yield 2;
    return 3;
    }

    // "generator function" creates "generator object"
    let generator = generateSequence();
    console.log(generator); // [object Generator]

    let one = generator.next();

    console.log(JSON.stringify(one)); // {value: 1, done: false}
    ```
    As of now, we got the first value only, and the function execution is on the second line:

    ```javascript
    let two = generator.next();

    console.log(JSON.stringify(two)); // {value: 2, done: false}
    ```

    And, if we call it a third time, the execution reaches the return statement that finishes the function:

    ```javascript
    let three = generator.next();

    alert(JSON.stringify(three)); // {value: 3, done: true}

    ```
    Now the generator is done. We should see it from done:true and process value:3 as the final result.

    Note: Generators are iterable.

-----

7. ### What are arrow functions in ES6

    Arrow functions allow us to write shorter function syntax. The handling of this is also different in arrow functions compared to regular functions. In regular functions the this keyword represented the object that called the function, which could be the window, the document, a button or whatever. With arrow functions the this keyword always represents the object that defined the arrow function.

    ```javascript
    //before
    hello = function() {
        return "Hello World!";
    }

    //after
    hello = () => {
        return "Hello World!";
    }
    ```
-----



