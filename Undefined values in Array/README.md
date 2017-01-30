See the next snippet of code:

	var aArr = [];
	aArr.length = 10;

	console.log(aArr);							// Shows [undefined, undefined, undefined, undefined, undefined, undefined, undefined, undefined, undefined, undefined] in the console.

	console.log( JSON.stringify( aArr[0] ) );	// Shows undefined in the console.


	console.log( JSON.stringify( aArr ) );		// Question 1

	console.log( aArr.toString() );				// Question 2

What will show the console in Question 1 ?  Why?

What will show the console in Question 2 ?  Why?


--Answer

In this example first Console.log will prompt:
	
	"[null,null,null,null,null,null,null,null,null,null]"
	
In the second example Console.log will prompt:

	",,,,,,,,,"
	 
Let me give you another exapmle; if we have array of ["1",2,3]:

	"[\"1\",2,3]"
	and
	"1,2,3"
	
ToString method will loose its type but jsonStrignify will keep its types so that we can reload copy of this array easily from it
Also keep in mind that json format does not support undefined values, there are nulls used instead
