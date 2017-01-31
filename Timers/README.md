When I execute this code:

	var check = false;
	var timeStart = new Date().getTime();

	setTimeout( function () {
		check = true;
	}, 1000 );

	while( !check ){
	}

	console.log( 'Loop has finished', 'Elapsed time:' + (new Date().getTime() - timeStart) );

When I will see the log in the console?

What will be the approximated value of the elapsed time?

Why?

--Answer

In JS there is Stack and Callback Queue. In stack function calls etc. stored. When a timer event executes it will drop on Callback queue. JS will not take anything from Callback Queue until stacks get completely emypty. 
While loop will continue to work, system will get stuck and callback will never get executed
