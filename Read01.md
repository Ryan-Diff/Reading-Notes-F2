# JS templates

    * Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them.

    * Syntax: 
        * `string text`

        `string text line 1
        string text line 2`

        `string text ${expression} string text`

        tag`string text ${expression} string text`

    * Template literals can contain placeholders. These are indicated by the dollar sign and curly braces (${expression}). The expressions in the placeholders and the text between the backticks (` `) get passed to a function

    * Multi line string:
        Any newline characters inserted in the source are part of the template literal.

        Using normal strings, you would have to use the following syntax in order to get multi-line strings:

        console.log('string text line 1\n' +
        'string text line 2');
        // "string text line 1
        // string text line 2"
        Using template literals, you can do the same like this:

        console.log(`string text line 1
        string text line 2`);
        // "string text line 1
        // string text line 2"

    * Expression interpolation:
        In order to embed expressions within normal strings, you would use the following syntax:

        let a = 5;
        let b = 10;
        console.log('Fifteen is ' + (a + b) + ' and\nnot ' + (2 * a + b) + '.');
        // "Fifteen is 15 and
        // not 20."
        Now, with template literals, you are able to make use of the syntactic sugar, making substitutions like this more readable:

        let a = 5;
        let b = 10;
        console.log(`Fifteen is ${a + b} and
        not ${2 * a + b}.`);
        // "Fifteen is 15 and
        // not 20."    

# Array Methods:

    * For each:
    * Syntax :arr.forEach(callback(currentValue [, index [, array]])[, thisArg]) 

    * forEach() calls a provided callback function once for each element in an array in ascending order. It is not invoked for index properties that have been deleted or are uninitialized. (For sparse arrays, see example below.)

    callback is invoked with three arguments:

    the value of the element
    the index of the element
    the Array object being traversed
    If a thisArg parameter is provided to forEach(), it will be used as callback's this value. The thisArg value ultimately observable by callback is determined according to the usual rules for determining the this seen by a function.

    The range of elements processed by forEach() is set before the first invocation of callback. Elements which are appended to the array after the call to forEach() begins will not be visited by callback. If existing elements of the array are changed or deleted, their value as passed to callback will be the value at the time forEach() visits them; elements that are deleted before being visited are not visited. If elements that are already visited are removed (e.g. using shift()) during the iteration, later elements will be skipped. (See this example, below.)

    forEach() executes the callback function once for each array element; unlike map() or reduce() it always returns the value undefined and is not chainable. The typical use case is to execute side effects at the end of a chain.

    forEach() does not mutate the array on which it is called. (However, callback may do so)     