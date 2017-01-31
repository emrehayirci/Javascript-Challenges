Look at the following "implementation" of a xor method on the prototype of the Boolean type.

	Boolean.prototype.xor = function (sValue) {return !!this !== !!sValue};

Now, why does the following statement resolve in an unexpected manner?

	false.xor (false) // => true

What can you do to fix it and what is the term that describes this behaviour?

## Bonus!!

If all of the following statements are true

	!!{} == true
	[] == false

Why does calling ...

	hasTruthyStuff([{},[] 0])

... on the following function return false?

	var hasTruthyStuff = function (aSymbols) {
		var nResult = 0,
			i = 0
			nLen = aSymbols.length;

		for (; i < nLen; i++) {
			nResult |= aSymbols[i];
		}
		return !!nResult;
	};

##Answer

	Boolean.prototype.xor = function (sValue) {return !!this !== !!sValue};
This statement is not negating value of this. It simply negating existance of this. To resolve this use this instead

	Boolean.prototype.xor = function (sValue) {return !!this.valueOf() !== !!sValue;};
	
###Bonus
Bitwise or and assigning its value has nothing to do with the existance of the values but values of the variables. So that 
for the each arguments their bitwise representations are 00000000000...0000 etc. You can test their values by [] << 0 statement. This statement simply bitwise lefts the statements. Therefore bitwise oring all of statements will result in 00000...0000 
