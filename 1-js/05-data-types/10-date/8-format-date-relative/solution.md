`tarih`'ten şimdiye kadar geçen süre -- tarihleri birbirinden çıkar.
```js run
function formatTarih(tarih) {
  let fark = new Date() - tarih; // Farkın ms. cinsinden değeri

  if (fark < 1000) { // 1 saniye önce
    return 'Şimdi';
  }

  let sn = Math.floor(fark / 1000); // farkı saniyeye çevir.

  if (sn < 60) {
    return sn + ' saniye önce';
  }

  let dk = Math.floor(fark / 60000); // farkı dakika çevir
  if (dk < 60) {
    return dk + ' dakika önce';
  }

  // tarihi formatla
  // ve geri kalan tek basamakları iki basamak haline getir.
  let d = date;
  d = [
    '0' + d.getDate(),
    '0' + (d.getMonth() + 1),
    '' + d.getFullYear(),
    '0' + d.getHours(),
    '0' + d.getMinutes()
  ].map(component => component.slice(-2)); // Her bileşenin son iki hanesini al.

  // bileşenleri tarihe ekle
  return d.slice(0, 3).join('.') + ' ' + d.slice(3).join(':');
}

alert( formatDate(new Date(new Date - 1)) ); // "Şimdi"

alert( formatDate(new Date(new Date - 30 * 1000)) ); // "30 saniye önce"

alert( formatDate(new Date(new Date - 5 * 60 * 1000)) ); // "5 dakika önce"

// dünün günü şu şekilde: 31.12.2016, 20:00
alert( formatDate(new Date(new Date - 86400 * 1000)) );
```
