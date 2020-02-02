![1.1](1.1.png)

![image-20200202212835642](image-20200202212835642.png)

![image-20200202212849717](image-20200202212849717.png)

![1.4](1.4.PNG)

![2.1](2.1.PNG)

![2.2](2.2.PNG)

![2.3](2.3.PNG)

![3.1](3.1.PNG)

![3.2](3.2.PNG)

![3.3](3.3.PNG)

![3.4](3.4.PNG)

![4.1](4.1.PNG)

![4.2](4.2.PNG)

![4.3](4.3.PNG)

![4.4](4.4.PNG)

![5.1](5.1.PNG)

![5.2](5.2.PNG)

![5.3](5.3.PNG)

![6.1](6.1.PNG)

Il chiffre p donc c = p^clef privée, donc gcd(c,N) = p . 

![6.2](6.2.PNG)

![7.1](7.1.PNG)

$91 = 7 * 13$ donc on utilise les restes chinois.  $ 70^{122448} \pmod 7 = 0 \pmod 7 $ et $70^{122448} \pmod {13} = 5 ^{122448} $  Comme mod premier avec exposant on peut travailler mod phi(7) et phi(13) dans l’exposant.  $122448 \pmod 6 = 0$ et $122448 \pmod 12 =  0 $ car sommes des chiffre divisible par 3 et il est pair.  Donc $  x \equiv 0 \pmod 7 $ et $ x \equiv 1 \pmod {13} $ donc le résultat vaut 14. 

![7.2](7.2.PNG)

On fait d’abord  $ (x^4 + x^2 ) \pmod {x^4 + x + 1 } = x^2 + x + 1$  puis on multiplie par l’inverse de $x^3 + 1 $  qui vaut $x$  ( évident) donc on obtient $(x^4 + x^2)x = x^5 + x^3 = x^3 + x^2 + x $  
