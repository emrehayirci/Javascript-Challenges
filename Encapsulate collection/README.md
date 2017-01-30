Having this code:

	function Order()
	{
			 this.aOrderLines = [];
			 this.nOrderTotal = 0;
	}
	Order.prototype.getOrderLines = function()
	{
			 return this.aOrderLines;
	};
	Order.prototype.addOrderLine = function(oOrderLine)
	{
			 this.nOrderTotal += oOrderLine.nTotal;
			 this.aOrderLines.push(oOrderLine);
	};
	Order.prototype.removeOrderLine = function(oOrderLineItem)
	{
			 var nOrderTotal;
			 oOrderLine = this.aOrderLines.map(function(oOrder)
			 {
					  return oOrder === oOrderLineItem;
			 })[0];

			 if(typeof oOrderLine === 'undefined' || oOrderLine === null)
			 {
					  return;
			 }
			 this.nOrderTotal -= oOrderLine.nTotal;
			 this.aOrderLines.splice(this.nOrderTotal, 1);
	};

The problem in this code is that anyone could access aOrderLines and add or modify values without increasing or decreasing nOrderTotal.

Keep in mind that you have to implement a method to get aOrderLines to loop over its items but avoiding to modify the values.

How you could solve this problem?

--Answer



	    f(function ()
    {
         var aOrderLines = [];
         var nOrderTotal = 0;
         getOrderLines = function()
         {
           return aOrderLines;
         };
         addOrderLine = function(oOrderLine)
         {
           nOrderTotal += oOrderLine.nTotal;
           aOrderLines.push(oOrderLine);
         };
         removeOrderLine = function(oOrderLineItem)
         {
           var nOrderTotal;
           oOrderLine = aOrderLines.map(function(oOrder)
           {
                    return oOrder === oOrderLineItem;
           })[0];
  
           if(typeof oOrderLine === 'undefined' || oOrderLine === null)
           {
                    return;
           }
           nOrderTotal -= oOrderLine.nTotal;
           aOrderLines.splice(nOrderTotal, 1);
           console.log(aOrderLines);
        };
    })();
    
Note that self invoking anonymous function expression used here. Therefore array and number cannot be reach because it remained in another scope
