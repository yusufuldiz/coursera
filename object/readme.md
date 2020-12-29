Javascript Object<br>
Javascript’in en temel veri tipi kabul edilen objeler, son derece önemlidir ve nasıl çalıştıklarını bilmek bir front-end developer için hayati önem taşır. Bu yazıda javascript objelerinin teorik çalışma mantığını örneklerle göreceksiniz.<br>
Objenin basit tanımı<br>
Objeler, içerisinde birden fazla değeri depolayan yapılardır. Property olarak bilinen bu değerler primitive(String,number, boolean vb.) veya başka objeler olabilirler ve her bir değer string veya sembol ile isimlendirilebilir.  
```javascript
let Artist = {
 name:"Zoé",
 album:{
  title:"Reptilectric",
  year:2008
 },
};
```
Objeler değiştirilebilen veri tiplerindendir. İçerdiği propertyler, obje’nin kendisi ```javascript const``` keywordüyle atanmış olsa bile değiştirilebilirler. Fakat primitive değerlerden farklı olarak objeler, referans yoluyla değiştirilirler ve değişen obje, yeni bir hafıza adresine sahip olur. Çünkü primitive değerlerin aksine objeler, javascript istemcisinin belleğinde, sahip oldukları değerlerle değil, sistemin atadığı hafıza adresleriyle kayıtlıdırlar. Bunun ayrımını aşağıdaki örnekte şöyle görebiliriz.
```javascript
//aynı değerlere sahip 2 primitive veri tipi
let mesaj = "merhaba";
let başkaBirMesaj = "merhaba";
console.log(mesaj == başkaBirMesaj);       //true

//aynı değerlere, farklı memory adresslere sahip 2 obje
let obje = {
 mesaj:"merhaba"
}
let başkaBirObje = {
 mesaj:"merhaba"
}
console.log(obje == başkaBirObje);         //false
```
Bu örnekte görüldüğü gibi, aynı primitive değerlere sahip olan “mesaj” ve “başkaBirMesaj” isimli değişkenler eşit kabul ediliyor. Fakat “obje” ve “başkaBirObje” isimli objeler de bire bir aynı değerleri barındırmalarına rağmen eşit kabul edilmiyorlar. Çünkü bu iki obje, arka planda göremediğimiz iki ayrı hafıza adresiyle tanınıyorlar, bu yüzden içerikleri aynı olsa da farklı kabul ediliyorlar. 

Obje oluşturmak<br>
Objeler üç şekilde oluşturulabilir. Object literal, new Object keyword’ü ve Object.create() foksiyonuyla. Object literal ve new Object yöntemleri, normal bir objeyi oluştururken kullanılan yöntemlerdir. Object.create() yöntemi ise, mevcut bir objeden kalıtım yoluyla bazı bilgiler alarak yeni bir obje oluşturmaya yarar. Aşağıdaki ilk örnekte, object literal ve new object yöntemleriyle birer obje oluşturalım;
```javascript
let countriesTalkSpanish = {
location: "south america",
language: "spanish"
};
 
let countriesTalkEnglish = new Object();
countriesTalkEnglish.location = "australia";
countriesTalkEnglish.language = "english"; 

```
Object literal yöntemiyle güney amerikada bulunup ispanyolca dilini konuşan ülkelerin genelini kapsayacak bir obje örneği oluşturduk. Tıpkı bunun gibi, avustralya kıtasında bulunan ve ingilizce konuşulan ülkeler için de new Object keywordünü kullanarak bir obje örneği oluşturduk. Şimdi, Object.create yöntemiyle, spesifik bir güney amerika ülkesi oluşturalım;
```javascript
let argentina = Object.create(countriesTalkSpanish);
argentina.capital = "buenos aires";
```
Object.create yöntemiyle argentina adında yeni bir obje oluşturduk. Bu obje, az önce oluşturduğumuz countriesTalkSpanish objesinin özelliklerini kalıtım yoluyla almış oldu. Objemizi yazdırdığımızda, sonradan eklediğimiz capital:"buenos aires" propertysinin yanı sıra, language:spanish ve location:south america propertylerine de kalıtım yoluyla sahip olduğunu görürüz.

