# Basit bir ntp client kodu
Aşağıdaki kod ile basit bir ntp-client yapılabilir. Bunun için `npm i ntp-client` modülünün kurulu olması gerekmektedir.

```js
var ntpClient = require('ntp-client');
// npm i ntp-client
 
ntpClient.getNetworkTime("0.tr.pool.ntp.org", 123, function(err, date) {
    if(err) {
        console.error(err);
        return;
    }
 
    /*console.log("Current time : ");
    console.log(date.getTime()); // Mon Jul 08 2013 21:31:31 GMT+0200 (Paris, Madrid (heure d’été))*/
    const tarih = new Date();
    tarih.setTime(date.getTime());
    console.log(tarih.getHours());
    console.log(tarih.getMinutes());
    console.log(tarih.getSeconds());
});
```
Sistem saatini değiştirmek için ise aşağıdaki komutlar kullanılır
```js
// npm i shelljs
var shell = require('shelljs');
shell.exec("timedatectl set-ntp false");
shell.exec("date -s '12:12:12'");
```
