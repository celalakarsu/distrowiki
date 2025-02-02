Derleme türleri
---------------
Paketler derlenirken farklı derleme araçları ve derleyiciler kullanılır. Bu bölümde kaynak kod derleme ile ilgili bilgiler verilecektir. Anlatım için C programlama dili ve gcc tercih edilecektir.

Bu bölümün amacı sizlere C kaynak kodlarının nasıl derlendiği ve nasıl çalıştığını anlatmaktır. C programlama dili ile ilgili yeterli bilginiz yoksa bu bölüme geçmeden önce bilgilerinizi gözden geçirmeyi öneririz.

Örneğin elimizde aşağıdaki gibi bir C dosyası bulunsun. Bu dosya derlenip bilgisayarın anlayabileceği hale getirilmek için **gcc**  kullanılarak derlenmelidir.

.. code-block:: C

	//main.c dosyası
	#include <stdio.h>
	int main(){
	    printf("Hello World\n");
	}

Bu dosyayı derleyip çalıştırılabilir dosya elde edelim.

.. code-block:: shell

	$ gcc -c main.c -o main.o
	$ gcc -o main main.o
	# .o oluşturmadan doğrudan da derleyebilirsiniz.
	$ gcc -o main main.c

Yukarıdaki örnekte kaynak kodu ilk önce **.o** uzantılı object dosyasına çevirdik. Daha sonra bu dosyadan çalıştırılabilir dosya ürettik.

Derlemeler **static** ve **dynamic** olarak 2 şekilde yapılabilir. Static olarak yapılan derleme herhangi bir bağımlılık olmaksızın çalışabilirken Dynamic olarak yapılmış derlemeler sistemdeki libc ve diğer gereken bağımlılıklara ihtiyaç duyar.
static derleme boyut olarak daha büyüktür ve gerekli olan kütüphanelerin static hallerinin de bulunması gerekir.

gcc libstdc++ Ekleme
--------------------

gcc ile derlenen bazı dosyalarda **libstdc++** görülür. Bu kütüphaneyi static olarak dahil etmek için **-static-libstdc++**
eklenmelidir.

.. code-block:: shell

	$ gcc -o main main.c -static-libstdc++ #statik kütüphane dahil edildi

.. raw:: pdf

   PageBreak

