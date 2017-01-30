Read the following snippets of code:

Snippet 1:

    var test;

    if ( true ) {
        test = function () {
            console.log( "That's true" );
        };
    } else {
        test = function () {
            console.log( "That's false" );
        };
    }

    test(); // Shows "That's true"

Snippet 2:

    if ( true ) {
        function test() {
            console.log( "That's true" );
        }
    } else {
        function test() {
            console.log( "That's false" );
        }
    }

    test(); // Shows "That's false"

Snippet 3:

    var test;

    if ( true ) {
        test = function () {
            console.log( "That's true" );
        };
    } else {
        function test() {
            console.log( "That's false" );
        }
    }

    test(); // Shows "That's true"


What's the reason of this behaviour?


--Answer
   
I tried doing this at different interpreters. This problem is exists on older verisons of js i guess . Defining  functions like snippet2 is not secure. Defining functions like snipet1 is much more secure.
At snipet2 hoisting will take place and replace our function no matter looking if else statement. 
