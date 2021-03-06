---
title: Подключение к SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 486d26dd3afeb91cb43181875e22592fb482af5f
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702803"
---
# <a name="connecting-to-sql-server"></a>Подключение к SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этой статье описывается, как можно создать подключение к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="connection-properties"></a>Свойства соединения  

Ключевые слова и атрибуты [строки](../../../connect/odbc/dsn-connection-string-attribute.md) подключения для всех ключевых слов и атрибутов строки подключения, поддерживаемых в Linux и Mac, см. в разделе.

> [!IMPORTANT]  
> При подключении к базе данных, которая использует зеркальное отображение базы данных (имеет партнера по обеспечению отработки отказа), не указывайте имя базы данных в строке подключения. Вместо этого отправьте команду **use** _имя_базы_данных_, чтобы подключиться к базе данных перед выполнением запросов.  
  
Значение, передаваемое в ключевое слово **Driver** , может быть одним из следующих:  
  
-   именем, использованным при установке драйвера;

-   путем к библиотеке драйвера, которая была указана в INI-файле шаблона, используемого для установки драйвера.  

Чтобы создать имя DSN, создайте (при необходимости) и измените файл **~/.ODBC.ini** (`.odbc.ini` в домашнем каталоге) для имени пользователя, доступного только для текущего пользователя, или `/etc/odbc.ini` для системного имени DSN (требуются права администратора). Ниже приведен пример файла, который показывает соответствующие записи для имени DSN:  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

При необходимости можно указать протокол и порт для подключения к серверу. Например, **Server = TCP:** _ServerName_ **, 12345**. Обратите внимание, что единственным протоколом, поддерживаемым драйверами `tcp`Linux и macOS, является.

Чтобы подключиться к именованному экземпляру через статический порт, используйте <b>Server=</b>*имя_сервера*,**номер_порта**. Подключение к динамическому порту не поддерживается в версиях ниже 17.4.

Кроме того, можно добавить сведения о DSN в файл шаблона и выполнить следующую команду, чтобы добавить его в `~/.odbc.ini`:
 - **odbcinst -i -s -f** _template_file_  
 
Можно проверить, работает ли драйвер с помощью `isql` для проверки подключения, или можно использовать следующую команду:
 - **bcp Master. INFORMATION_SCHEMA. Tables out of File. dat- <server> S- <name> U-P<password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Использование протокола SSL  
Можно использовать протокол SSL для шифрования соединения с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. SSL защищает имена пользователей и пароли [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сети. Кроме того, SSL проверяет идентификатор сервера для защиты от атак "злоумышленник в середине".  

Включение шифрования повышает безопасность за счет снижения производительности.

Дополнительные сведения см. [в разделе Шифрование соединений для SQL Server](https://go.microsoft.com/fwlink/?LinkId=220900) и [Использование шифрования без проверки](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).

Независимо от параметров для **Encrypt** и **TrustServerCertificate**учетные данные входа на сервер (имя пользователя и пароль) всегда шифруются. Следующая таблица показывает эффект от параметров **Encrypt** и **TrustServerCertificate** .  

||**TrustServerCertificate = нет**|**TrustServerCertificate = да**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|  
|**Encrypt=yes**|Сертификат сервера проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.<br /><br />Имя (или IP-адрес) в общем имени субъекта (CN) или альтернативном имени субъекта (SAN) в SSL-сертификате [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должно точно совпадать с именем сервера (или IP-адресом), указанным в строке подключения.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.|  

По умолчанию зашифрованные соединения всегда проверяют сертификат сервера. Однако при подключении к серверу, у которого есть самозаверяющий сертификат, также добавьте `TrustServerCertificate` параметр для обхода проверки сертификата по списку доверенных центров сертификации:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL использует библиотеку OpenSSL. Следующая таблица содержит минимально поддерживаемые версии OpenSSL, а также расположения хранилища доверия сертификатов по умолчанию для каждой платформы:

|Платформа|Минимальная версия OpenSSL|Расположение хранилища доверия сертификатов по умолчанию|  
|------------|---------------------------|--------------------------------------------|
|Debian 10|1.1.1|/etc/ssl/certs|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71|1.0.1|/etc/ssl/certs|
|OS X 10,11, macOS 10,12, 10,13, 10,14|1.0.2|/уср/локал/етк/опенссл/цертс|
|Red Hat Enterprise Linux 8|1.1.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 15|1.1.0|/etc/ssl/certs|
|SuSE Linux Enterprise 11, 12|1.0.1|/etc/ssl/certs|
|Ubuntu 18.10, 19.04|1.1.1|/etc/ssl/certs|
|Ubuntu 18.04|1.1.0|/etc/ssl/certs|
|Ubuntu 16.04, 16.10, 17.10|1.0.2|/etc/ssl/certs|
|Ubuntu 14.04|1.0.1|/etc/ssl/certs|

Также можно указать шифрование в строке подключения с помощью `Encrypt` параметра при использовании **SQLDriverConnect** для подключения.

## <a name="adjusting-the-tcp-keep-alive-settings"></a>Настройка параметров поддержания активности TCP

Начиная с ODBC Driver 17,4, как часто драйвер отправляет пакеты проверки активности и пересылает их, если ответ не получен, можно настроить.
Чтобы настроить, добавьте следующие параметры в раздел драйвера в `odbcinst.ini`или в раздел имени DSN в. `odbc.ini` При подключении с помощью имени DSN драйвер будет использовать параметры в разделе DSN, если они есть. в противном случае, или, если соединение выполняется только со строкой подключения, оно будет использовать параметры из раздела `odbcinst.ini`драйвера в. Если параметр отсутствует в обоих расположениях, драйвер использует значение по умолчанию.

- `KeepAlive=<integer>`Определяет, как часто TCP пытается проверить, что неактивное соединение остается неизменным, отправив пакет проверки активности. Значение по умолчанию — **30** секунд.

- `KeepAliveInterval=<integer>`Определяет интервал, разделяющий повторные передачи проверки активности до получения ответа.  Значение по умолчанию составляет **15** секунд.


## <a name="see-also"></a>См. также:  
[Установка Microsoft ODBC Driver for SQL Server в Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
