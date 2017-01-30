Copy and run, individually, the next lines of code in your console:

**console.log( 'mañana' === 'mañana' );**

**console.log( 'mañana' === 'mañana' );**

What logs each of them?

Why the result is different?

How you could avoid this issue?

--Answer

Lets look at 'ñ' letters in both side for second console.log :

    First word's ñ letter :
    U+006E : LATIN SMALL LETTER N
    U+0303 : COMBINING TILDE
    
    Second word's ñ letters
    U+00F1 : LATIN SMALL LETTER N WITH TILDE
 
If you try to console.log each of the words' lenght you will get 7 and 6.
In order to resolve this we must 'normalize' both strings
For further reading you can look at 

    https://developer.mozilla.org/tr/docs/Web/JavaScript/Reference/Global_Objects/String/normalize

How to solve this: 

      var first = 'mañana';
      var second = 'mañana';
      first = first.normalize('NFD');
      second = second.normalize('NFD');
      console.log(first === second);
