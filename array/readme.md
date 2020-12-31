## Array Methodları

Bugünkü yazıda array(dizi) methodlarından bahsedeceğiz. Methodları öğrenirken bilmemiz gereken bir şey: bazı methodlar, üzerinde işlem yapılan diziyi değiştirmeden yeni bir dizi oluşturarak bu yeni dizi üzerinde işlem yaparken, diğer methodlar doğrudan mevcut diziyi değiştirmesi. Array methodlarını türlerine göre 4’e ayırmak yanlış olmaz;<br>
-Yineleyici methodlar kısaca bir dizinin elemanlarını döngüye almamızı sağlar.<br>
-Yığma ve ekleme methodları bir dizinin başına/sonuna eleman eklememize yada dizinin başından/sonundan eleman çıkarmamıza olanak tanır. <br>
-Alt dizi yöntemleri, büyük bir dizinin bitişik kısımlarını ayıklamak, silmek,eklemek, doldurmak ve kopyalamak için vardır.<br>
-Arama ve sıralama yöntemleri, bir dizinin içindeki elemanları bulmak veya sıralamak için kullanılabilir.<br>


### Yineleyici methodlar
Bu methodlar, bir fonksiyona atanan parametreler yardımıyla dizinin elemanlarının dizileri yineler, eşler, filtreler, test eder, azaltır.<br>
Bu tür metodların hepsi, ilk argüman olarak bir fonksiyon alırlar ve dizideki bazı veya tüm elemanlar için ilgili fonksiyonu çağırırlar. Çoğu durumda, ilgili fonksiyon 3 argüman alır. Bunlar: dizinin elemanları, elemanların sıra numaraları ve dizinin kendisidir ve sıklıkla sadece ilk argümana ihtiyaç duyarız.

#### forEach()
Belirtilen fonksiyonu dizinin her bir elemanı için döner. Yukarıda belirtildiği gibi 3 argüman alır ve dizinin elemanlarını dönmek istediğimizde ilk argümanı girmek yeterli olacaktır.
```javascript
let kutu = ["cake","biscuit","orange juice","cracker"];
kutu.forEach(food => { console.log(food) });
```
forEach metodunu kullanarak kutunun içindeki elemanları yazdırdık. Parametre olarak sadece elemanları belirttik. Eleman parametresine  `food` adını verdik. 
forEach metodunda, tüm öğeler işleme aktarılmadan önce yinelemeyi durduracak bir yol yoktur. Yani normal bir for loop’ta kullanılan break ifadesinin eşdeğeri yoktur.
#### map()
Görünürde forEach ile oldukça benzer olsa da, map fonksiyonu mutlaka bir değer dönmek zorundadır. Ayrıca bu metod, mevcut diziyi değiştirmez, fonksiyon yeni bir dizi oluşturur. 
```javascript
let kutu = ["cake","biscuit","orange juice","cracker"];
kutu.map(food => food);
console.log kullanarak mevcut diziyi yazdırmadık, çünkü fonksiyon halihazırda bir değer döndü.
let sayilar = [2,4,6];
sayilar.map(value => value*value);              //4,16,36
console.log(sayilar)                                   //2,4,6 mevcut dizi değişmedi
```
#### filter()
Bir dizi içerisindeki elemanları, fonksiyonda belirtilen şartı karşılayıp karşılamamasına göre döndürür ve bir alt diziye ekler. İçerisinde 1’den 10’da kadar sayı bulunduran dizideki 5’ten büyük elemanları döndürmek gibi. 
```javascript
let sayilar = [2, 4, 6, 8, 10];
sayilar.filter(value => value > 6);              //8,10
console.log(sayilar);        //2,4,6,8,10  mevcut dizi değişmedi
```
#### find() ve findIndex()
filter() ile hemen hemen aynı işlevi görüyor diyebiliriz. Aralarındaki fark, find()’ın fonksiyonda belirtilen şartı sağlayan ilk elemanı dönmesi. findIndex() ise elemanın indexini(dizideki sıra numarasını) döner.
```javascript
let sayilar = [1,3,5,7,9];
sayilar.find(value => value % 3 == 0);   //3 //eğer filter kullansaydık 3,9 dönecekti.
sayilar.findIndex(value => value > 4); //2 //4’ten büyük olan ilk sayı(5) index değerini(2) aldık.
```
#### every() ve some()
every() ve some() metodları, fonksiyonda istenen şartlara göre true yada false döner. 
every() metodu, fonksiyonda istenen şartı, dizideki tüm elemanların karşılaması halinde true döner, aksi takdirde sonuç hep false olur.
```javascript
let ciftSayilar = [2,4,6,8];
ciftSayilar.every(value => value % 2 == 0);         //true
ciftSayilar.every(value => value > 5)                    //false
```
some() metodu, fonksiyonda istenen şartı, dizideki elemanlardan en az biri karşılıyorsa true, hiçbiri karşılamıyorsa false döner. 
```javascript
let elemanlar = [4,+6 ,"hi world"];
elemanlar.some(isFinite);  //true //dizide sonlu sayı olan elemanlar var.
elemanlar.some(value => value % 7 == 0); //false //dizide 7 ile tam bölünebilen bir eleman yok.
elemanlar.some(value => typeof value === "string"); //true //dizide tipi string olan eleman var.
```

