+++
title = "Настройка КриптоПро Рутокен под Ubuntu"
date = "2025-02-18T08:30:00+03:00"
#dateFormat = "2006-01-02" # This value can be configured for per-post date formatting
author = "ernado"
authorTwitter = "" #do not include @
cover = ""
tags = ["рутокен", "эцп", "ubuntu"]
keywords = ["рутокен", "эцп", "криптопро", "ubuntu", "CryptoPro"]
description = "Инструкция по настройке токена в Ubuntu"
showFullContent = false
readingTime = false
hideComments = false
+++

Я расскажу как настроить Рутокен с электронной подписью под Ubuntu, чтобы работать с ним в браузере.
Для этого нужно установить Крипто Про CSP и библиотеку для работы с токеном.

# Установка

## CryptoPro CSP

Достаточно воспользоваться инструкцией на сайте [Контур][kontur-crypto].

1. Зарегистрироваться на сайте [КриптоПро][registration].
2. Зайти в [загрузки][downloads].
3. Скачать установщик для Ubuntu через _Скачать для Linux DEB x64_.

И установить:
```bash
cd ~/Downloads
tar -xvf linux-amd64_deb.tgz
cd linux-amd64_deb/
./install_gui.sh
```

Значений по умолчанию будет достаточно.

[registration]: https://cryptopro.ru/user/register
[downloads]: https://cryptopro.ru/products/csp/downloads
[kontur-crypto]: https://support.kontur.ru/ca/38828-ustanovka_kriptopro_csp_na_ubuntu

## Рутокен

Затем нужно обязательно установить библиотеку для работы с токеном.
Заходим на сайт [Рутокен][rutoken] и скачиваем [Библиотека rtPKCS11ecp для GNU/Linux DEB 64bit.][rtpkcs11ecp].
После этого устанавливаем через `apt install`:

```bash
cd ~/Downloads
wget https://download.rutoken.ru/Rutoken/PKCS11Lib/2.17.1.0/Linux/x64/librtpkcs11ecp_2.17.1.0-1_amd64.deb
sudo apt install ./librtpkcs11ecp_2.17.1.0-1_amd64.deb
```

[rutoken]: https://www.rutoken.ru/support/download/pkcs/
[rtpkcs11ecp]: https://www.rutoken.ru/support/download/get/rtPKCS11-deb-x64.html

## Расширение для браузера

Я использую Яндекс.Браузер для работы с токеном, это оказалось удобнее всего, так как плагин для Google Chrome у
меня не установился, а в расширениях найти его не удалось.

Расширение я устанавливал вручную через [аддоны для оперы][opera-crypto-pro].

Альтернативно, можно [собрать браузер Яндекс][yandex-build] для организаций с поддержкой этого расширения.

[opera-crypto-pro]: https://addons.opera.com/en/extensions/details/cryptopro-extension-for-cades-browser-plug-in/
[yandex-build]: https://browser.yandex.ru/corp/build/a71eb434-ad93-4392-9dc5-450a33c093bc?banerid=6301000000&switch=1

### Проверка

Заходим на [тестовую страницу CryptoPro][cades-sample] и проверяем, что всё работает.
Если всё установлено правильно, то в списке доступных сертификатов появится наш.

Если всё кроме сертификата есть, то нужно убедиться, что библиотека для Рутокен установлена.

[cades-sample]: https://www.cryptopro.ru/sites/default/files/products/cades/demopage/cades_bes_sample.html
