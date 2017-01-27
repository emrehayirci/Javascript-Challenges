As you know Javascript has two different ways to treat the data it receives as arguments of a function:

* Primitives are passed by copy
* Complex Objects are passed by reference.

This mini-challenge is related with this topic.

	var oPerson = { name: 'john'};						// Define an object

	(function(oTeacher) {								// Create a closure to use the object in other function code.
	   window.getTeacher= function() {
		  console.log(oTeacher);
	   };
	}(oPerson));

	window.getTeacher();								// Get the teacher.

	oPerson.surname = 'doe';							// Augment the object.

	window.getTeacher();								// Get the teacher again.

	oPerson = { name: 'mary', surname: 'sullivan' };	// Redefine an object

	window.getTeacher();								// Get the teacher again.

The first execution of window.getTeacher returns:

	Object {name: "john"}

The second execution of window.getTeacher returns:

	Object {name: "john", surname: "doe"}

The third execution of window.getTeacher returns:

	Object {name: "john", surname: "doe"}

Can you explain what's the reason of this behaviour?

Can you see any problem about this behaviour?

How you could solve it?


--Answer
	Well this is one awesome question. Well here it works:
	
	1- oPerson is a global reference variable. It holds reference to the object { name: 'john'};
	
	2- We have an unnamed function that assigns a function on window. And assigned function's name is getTeacher. Notice that our unnamed functions takes an argument. This argument named oTeacher. After our unnamed functions decleration we are immidately calling itself with argument oPerson. Since oPerson is a refference it will Passed By Copying. So that our function getTeacher will console.log({REFERENCE ADRESS OF OUR INITIAL oPerson VARIABLE})
	
	3- If we execute getTeacher it will prompt our oPerson variable
	
	4- Now we are adding something to our oPerson variable. Since our oPerson object still pointing same adress as our getTeacher function we can see whatever we change , add in it.
	
	5- If we execute getTeacher it will prompt our oPerson variable
	
	6- Now things are getting messy! We are creating a new object and passing its refference to our oPerson variable! Note that our oPerson variable now wont be pointing same object as our getTeacher method's oTeacher variable. They are different things right now!
	
How to resolve this?
	Well first of all this is not an issue. This is a necessary part for js. Imagine you are iterating through bunch of nodes in graph; you probably use the same technique
	
	If we want our program to prompt marry instead of john we can change our initial function like this:
	
		  window.getTeacher= function() {
		  console.log(window.oPerson); 
		  };
	
	Unwrap and set it free :)
	
