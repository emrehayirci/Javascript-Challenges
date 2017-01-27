Try this in your console:

	function test(){ alert('test');}();

What happens?

Why?

How you could execute it only adding one more character to the sentence?

Explain why it works?

--Answer
	Bu fonksiyon otomatik çağıran fonksiyondur. Burada olan olayları özetlemek gerekirse "test" stringini alert eden bir tane isimsiz fonksyon yaratıyoruz. Daha sonra bu fonksyonu yaratılır yaratılmaz çağırıyoruz. 
	Daha sonradan bu alert mesajını değiştirilmesi, modifiye edilmesi imkansızdır. Bu fonksiyonda alert mesajını değiştirebilmek için :
		
		function test(x){ alert(x);}("differentalert");
		
	Şeklinde bir fonksiyon çağırımı yapılabilir.
