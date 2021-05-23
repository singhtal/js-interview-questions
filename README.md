# Complete JavaScript Interview Questions & Answers

> Click :star:if you like the project. Pull Requests are highly appreciated. Follow
> [@iamtalvinder](https://www.linkedin.com/in/iamtalvinder/) for more frontend insights.

### Table of Contents

| No. | Questions                                                                                           |
| --- | --------------------------------------------------------------------------------------------------- |
| 1   | [What are the primitive data types in javascript](#what-are-the-primitive-data-types-in-javascript) |
| 2   | [What is the symbol data type](#what-is-the-symbol-data-type)|
| 3   | [What is the difference between null and undefined](#what-is-the-difference-between-null-and-undefined)| 

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




